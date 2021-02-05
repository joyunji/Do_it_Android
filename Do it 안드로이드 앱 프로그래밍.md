Do it 안드로이드 앱 프로그래밍
======

목차
----
## 1. 뷰(View)

### 뷰 정렬하기

![unnamed](https://user-images.githubusercontent.com/49296139/107012291-2e2b7c80-67dc-11eb-9185-6c264c49f468.jpg)


## 2. 레이아웃(Layout)
대표적인 5가지의 레이아웃
### 1. 제약(ConstraintLayout)
    - 제약 조건 기반 모델
    - 제약 조건을 사용해 화면을 구성하는 방법
    - 안드로이드 스튜디오에서 자동으로 설정하는 디폴트 레이아웃
    
### 2. 리니어(LinearLayout)
    - 박스 모델
    - 한 쪽 방향으로 차례대로 뷰를 추가하며 화면을 구성하는 방법(Horizontal, Vertical)
    - 뷰가 차지할 수 있는 사각형 영역을 할당

#### 필수 속성
layout_width<br>
layout_height<br>
orientation: horizontal, vertical 

#### 자바 코드에서 화면 구성 예


~~~java
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        //new 연산자로 리니어 레이아웃을 만들고 방향 설정
        LinearLayout mainLayout = new LinearLayout(this);
        mainLayout.setOrientation(LinearLayout.VERTICAL);

        //new 연산자로 레이아웃 안에 추가될 뷰들에 설정할 파라미터 생성
        LinearLayout.LayoutParams params = new LinearLayout.LayoutParams(
          LinearLayout.LayoutParams.MATCH_PARENT,
          LinearLayout.LayoutParams.WRAP_CONTENT
        );

        //버튼에 파라미터 설정하고 레이아웃에 추가
        Button button1 = new Button(this);
        button1.setText("Button1");
        button1.setLayoutParams(params);
        mainLayout.addView(button1);

        setContentView(mainLayout);
    }
~~~

* context 객체:this<br>
: 뷰에 대한 정보를 손쉽게 확인하거나 설정할 수 있독 뷰의 생성자에 Context 객체를 전달

* LayoutParams 객체<br>
: 레이아웃에 추가되는 뷰의 레이아웃과 관련된 속성을 담고 있음.
반드시 뷰의 가로와 세로 속성을 지정해야 한다. 

#### 뷰 정렬하기
##### 정렬 속성
layout_gravity: 부모 컨네이너의 여유공간 안에서 뷰를 정렬함.<br>
gravity: 뷰 안에 표시하는 내용물(텍스트뷰 안의 텍스트, 이미지뷰 안의 이미지...)을 정렬함
baselineAligned: 뷰안의 텍스트끼리의 정렬

#### padding & margine

![view](https://user-images.githubusercontent.com/49296139/107012772-ccb7dd80-67dc-11eb-9945-c4450b2eee73.jpg)

### layout_weight 
: 부모 컨테이너에 남아있는 여유 공간을 분할하여 기존에 추가했던 뷰들에게 할당
--> 뷰에 지정한 크기에 추가되는 값

-----------------------------------------

### 3. 상대(RelativeLayout)
    - 규칙 기반 모델
    - 부모 컨테이너나 다른 뷰와의 상대적 위치로 화면을 구성하는 방법
    - 제약 레이아웃을 사용하게 되면서 상대 레이아웃은 권장하지 않음
    > 제약 레이아웃은 상대 레이아웃의 특성은 그대로 가지고 있으면서 더 많은 기능을 제공하기 때문.
    
#### 속성
- layout_above
- layout_below

### 4. 프레임(FrameLayout)
    - 싱글 모델
    - 가장 상위에 있는 하나의 뷰 또는 뷰 그룹만 보여주는 방법
    - 여러 개의 뷰가 들어가면 중첩하여 쌓게 됨. 가장 단순하지만 여러 개의 뷰를 중첩한 후 
    각 뷰를 전환하여 보여주는 방식으로 자주 사용함
### 5. 테이블(TableLayout)
    - 격자 모델
    - 격자 모양의 배열을 사용하여 화면을 구성하는 방법
    - HTML에서 많이 사용하는 정렬 방식과 유사하지만 많이 사용하진 않음
    > 제약 레이아웃과 리니어 레이아웃으로도 화면 배치 가능하기 때문.
    

    
