#Element 노드 지오메트리와 스크롤링 지오메트리
## 1. Element 노드 크기, 오프셋, 스크롤링 개요
> HTML 문서를 웹 브라우저에서 볼 때, DOM 노드가 해석되어 시각적인 모양으로 그려진다.
> 노드는 브라우저에서 볼 수 있는 시각적인 표현 형태를 가지고 있다.
> 노드의 시각적인 형태와 지오메트리를 프로그래밍을 통해 살펴보고 조각하기 위해 일련의 API들이 존재

## 2. offsetParent를 기준으로 element의 offsetTop 및 offsetLeft 값을 가져오기
> offsetTop 및 offsetLeft 속성을 사용하면, offsetParent로 부터 element 노드의 오프셋 픽셀 값을 가져올 수 있다.  
> element 노드 속성들은 element의 바깥쪽 좌상단 경계로부터 offsetParent의 안쪽 좌상단 경계까지의 거리를 픽셀로 제공해 준다.

## 3. getBoundingClientRect()를 사용하여 뷰포트를 기준으로 element의 Top, Right, Bottom, Left 테두리 오프셋을 얻기
> getBoundingClientRect() 메서드를 사용하면, 뷰포트의 좌상단 끝을 기준으로 element가 브라우저에서 그려질 때 element의 바깥쪽 테두리 위치를 얻을 수 있다.

## 4. 뷰포트에서 element의 크기(테두리 + 패딩 + 내용) 얻기
> getBoundingClientRect() 메서드는 top, right, bottom, left 속성/값뿐만 아니라 height와 width 속성/값도 가지고 있는 개체를 반환
> height와 width 속성은 element의 크기를 가리키는데, 전체 크기는 border-box 이다.  
> offsetHeight,offsetWidth 도 동일한 효과

## 5. 뷰포트에서 테두리를 제외한 element의 크기(패딩 + 내용) 얻기
> clientWidth , clientHeight 속성은 테두리 크기를 제외하고 element의 내용과 패딩을 더해서 element의 전체 크기를 반환 

## 6. elementFromPoint()를 사용하여 뷰포트의 특정 지점에서 최상단 element 얻기
> elementFromPoint()를 사용하면 HTML 문서의 특정 지점에서 최상단 element에 대한 참조를 얻을 수 있다.  
> 해당 위치에 두 개의 <div>가 있을경우 최상단 div가 선택된다.

## 7. scrollHeight와 scrollWidth를 사용하여 스크롤될 element의 크기를 얻기
> scrollHeight와 scrollWidth 속성은 스크롤될 노드의 높이와 너비를 제공해준다.

## 8. scrollTop과 scrollLeft를 사용하여 top 및 left로부터 스크롤될 픽셀을 가져오거나 설정하기
> scrollTop과 scrollLeft 속성은 스크롤 때무에 현재 뷰포토에서 보이지 않는 left나 top까지의 픽셀을 반환한다.

## 9. scrollIntoView()를 사용하여 element를 View로 스크롤하기
> 스크롤이 가능한 노드 내에 있는 노드를 선택하면, scrollIntoView() 메서드를 사용하여 선택된 노드가 view로 스크롤되도록 할 수 있다.

## ex01)
```javascript
document.querySelector(".ck-target").style="position:relative;"
var offsetTop = document.querySelector(".ck-target-sentence.ck-similar").offsetTop
document.querySelector(".ck-target").scrollTop = offsetTop
```
## ex02)
```javascript
document.querySelector(".ck-target > div").children[20].scrollIntoView()
```
