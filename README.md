# For-people Project
![](https://img.shields.io/badge/license-MIT-brightgreen)
![](https://img.shields.io/badge/HTML-5-orange)
![](https://img.shields.io/badge/css-3-blue)
![](https://img.shields.io/badge/team-awesome-red)
![](https://img.shields.io/badge/documentation-yes-green)

  최신 HTML5와 CSS3로만 구현한 카페 웹사이트
 

## 프로젝트 소개

  3주간 배웠던 HTML5, CSS3를 활용하여 카페형 웹사이트를 디자인 시안을 가지고 마크업부터 디자인까지 모두 해봄으로서 그 동안의 개인의 **학습 성과를 알아보기 위함**입니다. 
  또한 **웹접근성, SEO, 유저를 고려**한 레이아웃을 설계하는 것을 실습해보기 위한 것이었습니다. 마지막으로 **git을 활용하여 협업**하는 것을 학습하기 위함이었습니다. 


### 사용된 기술
![HTML5](./images/md/html5_logo.png)  ![CSS3](./images/md/css3_logo.png)   ![Git](./images/md/git_1.png )

최신 HTML5, CSS3기술을 사용하여 만들었습니다. 

### 지원 브라우저
- chrome
- IE11
- Firefox
- safari

### 팀원 소개
- [박혜준](https://github.com/margu31)
- [장원준](https://github.com/Wonjuny0804)
- [김지원](https://github.com/iamkjw77)
- [배근아](https://github.com/green9930)
  
## 프로젝트 진행 사항 소개
1. 구상 및 회의
2. 마크업 및 코딩 컨벤션
3. CSS 디자인
4. 코드 리뷰

### 팀의 방향성 설정
- [웹접근성](https://www.w3.org/WAI/fundamentals/accessibility-intro/)
- [SEO](https://en.wikipedia.org/wiki/Search_engine_optimization)
- [git 활용]()
- 유저 friendly

### 클래스 네이밍
 본 프로젝트에서는 각 클래스네이밍에 [BEM표기법](http://getbem.com/)을 사용하였다. 
### CSS 디자인

### 코드 리뷰
- CSS 모듈화
- 중복코드 삭제 및 코드 간소화
- 주석처리
- lighthouse 검사 및 피드백을 통한 수정
- 배포용 버전 디렉토리 생성
### 팀원별 개발 과정
#### 장원준

1. sign up 페이지
전체적인 팀의 개발 방향을 정하고나서 signup페이지를 마크업하기 시작했다. 마크업은 다음과 같은 순서로 진행하였다. 
      1. 논리적인 흐름구상
      2. 전체적인 페이지의 흐름, 용도를 파악하며 html tag를 결정
      3. 팀에서 정한 컨벤션으로 클래스 이름을 부여
      4. 복수 클래스가 있는지 확인
      5. html문서로 작성
      6. css 디자인

sign up페이지에서 어려웠던 부부은 많이 있었지만 가장 기억에 남는 부분은 크게 두 가지가 있다.
먼저 선택적 정보 동의 체크 버튼을 시안대로 디자인하는 과정에서 발생했던 문제였다. 

**문제점**
시안에서는 체크박스가 체크되었을때 시안 체크박스의 전후 요소의 색이 다르도록 설정되어 있었다. 
이를 해결하려고 span요소를 생성하고 span::after를 생성해서 두 요소를 시안과 같은 디자인으로 만들었다. 그래서 전후 요소에 같은 색을 주고 `opacity`를 시안대로 0.6으로 설정하였다. 그랬더니 span과 span::after모두 같은 색이 되었다. 아무리 색을 다르게 줘도 같은 색을 나타낼 뿐이었다. 
```css
background: #abcd3;
opacity: .6;
```
![](./images/md/check-switch-before.png)

**해결방법**
opacity는 속성 값으로 들어간 요소의 자식요소에게 상속되는 속성이다. 그렇기 때문에 자식요소가 다른 opacity값을 가져도 그 값은 들어가지 않는다. 따라서 opacity속성을 삭제하고 두 요소에 서로 다른 색상을 주는 방법도 있지만. opacity 속성과 동일한 rgba(0,0,0,0.6)으로 색 속성을 바꿔주면된다. rgba에서 마지막 알파채널을 통해서 투명도를 지정할 수 있고 이는 0과 1사이의 값을 주면된다. 자식 요소에 상속되서 생기는 문제점을 해결할 수 있다.
```css
background: rgba( 0,0,0, 0.6);
``` 
![](./images/md/check-switch-after.png)

두번째 발생했던 문제는 placeholder에 발생했던 문제였다. placeholder는 그 특성상 보조기기에서 읽어주지 않고 또한 input요소에 focus를 주고 입력함과 동시에 힌트가 사라지는 문제가 존재했다. 이러한 부분은 저시력자 또 힌트가 너무 긴경우 어려움을 줄 수 있어서 이 부분을 해결하려고 했고 실제 다른 회사들은 이 문제를 어떻게 해결했는지 벤치마킹해보았다. 

그러한 회사 중 하나가 바로 apple인데 apple은 다음과 같이 문제를 해결한 듯 하다. 
![](./images/md/placeholder-apple.png)

상단에서 보이는 것처럼 마우스 포커스가 올라가면 안에 있던 '힌트' 또는 '레이블'이 상부로 작아지면서 이동하는 것을 볼 수 있다. 이렇게 해줌으로서 시각적인 힌트를 사라지지 않고 계속해서 사용할 수 있으며 또한 시각장애인 분들이 input요소에 대한 힌트를 들을 수 있게 해줄 수 있다.

### 마치며

- 접근성 - 사실 컴공4년을 다니면서 한번도 들어보지 못했던 개념이다. 접근성은 단연 개발자에게 있어서 중요한 고려 요소이다. 기술이 발전함에 따라 많은 사람들이 그 혜택을 누리지만 또 그것을 누리지 못하는 이들이 있고 그들도 이 기술과 웹이라는 세상에 접근할 수 있도록 돕는 연결다리 역할을 하는 것이 개발자의 역할이라는 생각이 들었다. 시대가 지나고 기술이 변해도 접근성은, 더 나아가 기술자로서 세상을 더욱 연결되게해주고 서로가 더 가까워질 수 있도록 돕는 역할은 변하지 않을 것이라고 생각하게된 굉장히 중요한 부분이었다. 
- 퍼포먼스 - 결국 사용자에게 더 쾌적한 환경을 제공하기 위해서 최적화, 또 preload등을 활용했는데 이번 프로젝트는 이러한 렌더링과 서비스의 작동 퍼포먼스에 대해서도 계속 고민하게 만들었다. 
- 협업 - 깃을 통해서 처음으로 협업했던 이번 프로젝트는 git이 얼마나 유용한지 알게해줬고 팀장으로서 충돌이 났을때 해결하는 방법을 익히는 아주 유익한 시간이었다. 다음부터는 `git flow feature start`를 정말 작은 모듈 단위로 해야겠다는 생각이 들었고 협업을 할때도 팀원들에게 일정 시간이 지나면 선 pull 후 commit,push를 하도록 요청해야한다는 **중요한** 교훈을 깨닫게해준 프로젝트였다.