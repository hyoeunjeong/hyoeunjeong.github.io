# 🧠 Django 클래스 기반 뷰(CBV) vs 함수 기반 뷰(FBV) — 진짜로 뭐가 더 좋은 코드일까?

 **FBV와 CBV의 차이점, 장단점, 실제 사용 기준**

---

## 🧩 1. FBV — 전통적이고 직관적인 함수 기반 뷰

```python
from django.http import HttpResponse

def hello(request):
    return HttpResponse("Hello, FBV!")
```

- `request`를 받아서 직접 처리
- HTTP 메서드(GET, POST 등)를 `if` 문으로 구분
- 코드 흐름이 눈에 다 보이기 때문에 **초보자에게 매우 익숙한 구조**

예시: GET과 POST 처리

```python
def post_view(request):
    if request.method == 'GET':
        return render(request, 'form.html')
    elif request.method == 'POST':
        # 처리 로직
        return redirect('success')
```

---

## 🧱 2. CBV — 구조화된 클래스 기반 뷰

```python
from django.views import View
from django.http import HttpResponse

class HelloView(View):
    def get(self, request):
        return HttpResponse("Hello, CBV!")
```

- 클래스 단위로 뷰 작성
- 각 HTTP 메서드에 맞춰 `get()`, `post()` 메서드 오버라이딩
- 코드 재사용성과 확장성이 뛰어남
- Django가 기본 제공하는 **제너릭 뷰** 덕분에 CRUD 같은 반복 작업을 효율적으로 구현 가능

예시: 제너릭 CreateView

```python
from django.views.generic import CreateView
from .models import Post

class PostCreateView(CreateView):
    model = Post
    fields = ['title', 'content']
    template_name = 'post_form.html'
    success_url = '/posts/'
```

---

## ⚔️ 3. FBV vs CBV 직접 비교

| 항목             | 함수 기반 뷰 (FBV)                                 | 클래스 기반 뷰 (CBV)                                |
|------------------|---------------------------------------------------|----------------------------------------------------|
| **구조**         | 절차 지향, 간단한 함수 하나로 처리                  | 객체 지향, 클래스와 메서드로 처리                    |
| **초기 난이도**  | 쉬움, 바로 코드 작성 가능                           | 다소 어려움, 상속 구조와 메서드 이해 필요             |
| **가독성**       | 단순할 땐 뛰어남, 로직이 복잡해지면 비효율           | 처음은 어렵지만, 구조화되어 유지보수에 유리            |
| **재사용성**     | 낮음, 반복되는 로직 많아짐                          | 높음, Mixin으로 기능 분리 및 재사용 가능               |
| **확장성**       | 적음, 조건문 많이 들어가면 유지보수 어려움          | 높음, 제너릭 뷰와 Mixin으로 확장 가능                  |
| **디버깅**       | 실행 흐름이 명확해서 디버깅 쉬움                     | 상속 구조 따라가야 해서 초반엔 디버깅 어려울 수 있음     |

---

## 🧠 4. 실제 사용 예시

#### ✅ FBV 방식

```python
def post_list(request):
    posts = Post.objects.all()
    return render(request, 'post_list.html', {'posts': posts})
```

#### ✅ CBV 방식 (ListView)

```python
from django.views.generic import ListView
from .models import Post

class PostListView(ListView):
    model = Post
    template_name = 'post_list.html'
    context_object_name = 'posts'
```

---

## 🔄 5. 언제 FBV? 언제 CBV?

### 💡 FBV를 쓰면 좋은 경우
- 페이지 단위 뷰가 단순한 경우 (홈 화면, 연락처 등)
- 빠르게 개발하고 싶은 경우
- Python 초보자거나 함수형 코드가 익숙한 경우

### 💡 CBV를 쓰면 좋은 경우
- 반복되는 CRUD 로직이 많을 때
- 로그인/권한/접근제어 같은 공통 기능을 재사용하고 싶을 때
- 유지보수와 협업을 고려한 구조가 필요할 때

---

## 🧬 6. CBV가 진짜 강력해지는 순간: 믹스인(Mixin)

CBV의 진짜 힘은 Mixin으로 확장 가능한 구조에 있습니다.

```python
from django.contrib.auth.mixins import LoginRequiredMixin
from django.views.generic import UpdateView

class PostUpdateView(LoginRequiredMixin, UpdateView):
    model = Post
    fields = ['title', 'content']
    template_name = 'post_form.html'
    success_url = '/posts/'
```

- `LoginRequiredMixin`은 로그인 안 한 사용자가 접근할 수 없게 만들어줌
- 뷰마다 조건문으로 검사할 필요 없이 깔끔하게 처리됨

---

## ✅ 결론: “정답은 없다, 상황에 따라 알아서 잘 쓰자”

| 상황                          | 추천 구조 |
|-------------------------------|-----------|
| 단순한 뷰, 빠른 개발 필요        | FBV        |
| 구조화된 코드, CRUD 반복 처리     | CBV        |
| 재사용과 확장 고려해야 할 때      | CBV        |
| 로직 흐름이 직관적으로 보여야 할 때 | FBV        |

---

