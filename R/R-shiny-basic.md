# R-Shiny 기본
[참고]https://mrchypark.github.io/dabrp_classnote3/class8#1

### ~Input()함수, ~Output()함수 
* ~Input( ) 은 sidebarPanel( )에 위치
    * textInput( ), selectInput( ), numericInput( )
* ~Output( )은 mainPanel( )에 위치
    * dataTableOutput( ), plotOutput( ), tableOutput( ), textOutput( ) 등


```R
fluidPage(
  titlePanel("test"),
  sidebarLayout(
    sidebarPanel(
      sliderInput(
          inputId = "slider1"
        , label = "Slider"
        , min = 0
        , max = 100
        , value = 50
        )
    ),
    mainPanel("mainPanel Area")
  )
)
```


```R
fluidPage(
  titlePanel("test"),
  sidebarLayout(
    sidebarPanel(
      sliderInput(
          inputId = "slider1"
        , label = "Slider"
        , min = 0
        , max = 100
        , value = 50
      )
    ),
    mainPanel(
      plotOutput(
        outputId = "plot1"
      )
    )
  )
)
```

### 각 변수의 Id
Input()함수와 Output()함수는 사용할 변수에 대해 Id를 입력받는다. <br>
전부 글자형(character)로 구성된다. 
* InputId는 서버에서 input＄inputId 의 형태로 사용함. <br>
* outputId는 서버에서 만든 결과물을 전달 받기 위해서 사용하며 서버에서 저장할 때는 output＄outputId 로 사용. <br>


```R
# inputId
sliderInput(inputId = "slider1", label = "Slider", min = 0, max = 100, value = 50)
# outputId
plotOutput(outputId = "plot1")
```


### server만들기
server는 위에 Input()함수로 입력받은 데이터를 사용하기 위한 input변수와 Output()함수로 출력하기 위한 결과물을 저장하는 output변수, <br>
마지막으로 출력 결과물인 R객체를 web의 세상에서 사용할 수 있는 상태로 output변수에 저장하는 render*({}) 함수로 구성된다. <br>



```R
server <- function(input, output){
  output$plot1 <- renderPlot({
    plot(input$slider1)
  })
}
```

-----------------------------------------------------------------------
### shiny의 입출력
shiny는 웹 기술을 R로 사용할 수 있게 만드는 덕분에 render라는 과정이 필요하다. <br>
그래서 render 환경에서 변수들이 관리되어야 한다. 입출력은 input변수와 output변수로 관리한다. <br>
이 두가지는 render밖에서 관리되는 변수로 다르게 취급해야 한다.
* input : 웹 페이지의 입력을 통해서 들어오는 데이터를 사용하기 위한 변수
* output : 웹 페이지에 R 연산 결과물을 전달하기 위해 사용하는 변수


### render*({})
render*({}) 함수 안에는 plot함수가 R문법으로 작성되어 있다. 그리고 render*({}) 의 특이한 점은 ()안에 {}가 또 있다는 점. <br>
여기서는 ({}) 안쪽은 R의 세계이고, 그 바깥은 웹의 세계라고 이해하면됨.  <br>

#### *output( )* 함수에 대응되는 *render( )* 함수가 모두 있다. <br>
textOutput() 은 renderText() <br> 
plotOutput() 은 renderPlot()  등 ..


```R
server <- function(input, output) {

output$mpgPlot <- renderPlot({
    boxplot(as.formula(formulaText()),
            data = mpgData,
            outline = input$outliers,
            col = "#75AADB", pch = 19)
  })
    
}
```

### output ＄
output 변수는 list라고 이해하시면 된다. list인 output 변수는 output＄뒤에 변수명을 작성함으로써 output 객체에 필요한 결과물을 전달한다.<br>
만약에 화면에 보여줘야할 것의 이름을 sample이라고 하면 output＄sample에 필요한 내용을 선언하는 것으로 진행

### input ＄
input＄은 output＄과 같이 웹의 세계에 있는 변수이다. <br>
그래서 ~Input() 함수들을 통해서 input＄의 컬럼 이름으로 웹 페이지 내에서 얻을 수 있는 데이터를 R의 세계에서 사용할 수 있게 해준다.<br>



```R
sliderInput("sdata1", "슬라이더 입력:", min=50, max=150, value=100)
```

위의 코드는 sliderInput()이라는 ~Input() 패밀리 함수를 통해서 input＄sdata1이라는 곳에 웹 데이터를 저장하는 것을 뜻함

--------------------
### reactive({}) 함수
reactive는 반응성으로 번역하기도 한다. 반응성이라고 하는 이유는 input＄bins의 값이 변하는 순간을 render({})가 감지해서 <br>
변한 값을 반영하여 output＄distPlot에 저장하고, 그것을 plotOutput("distPlot")으로 전달하여 그림을 새로 그리기 때문이다. <br>
input의 변화에 반응하여 output이 변화하니 간단한 반응성으로 연결된 것

### 이외의 반응형 함수
* isolate() 
    * 즉각적인 반응이 아니라 어떤 다른 사용자의 입력(ex> action 버튼)을 인지하여 그 때 input에 해당하는 부분을 확인하여 결과물을 만듭니다. 
    render*({})함수 내부에서 사용합니다.

* observeEvent({}), eventReactive({})
    * 어떤 input을 인지하여 동작합니다. observeEvent({})는 서버 부분에서 실행해야 할 것들을 담당하기 때문에 선언의 형태가 아니라 독립적으로 작성됩니다. 
    예를 들어 서버에 파일을 저장한다거나, 로그로 남기는 글자를 출력하거나 할 때 사용합니다.
    
* eventReactive({})
    * reactive({})와 같이 웹의 세상의 변수에 선언하면서 함수화하여 R의 세상에서 반응형 데이터로써 사용할 수 있습니다.
    
* reactiveValues({})
    * input＄이나 output＄과 같은 역할을 하는 변수를 만드는 함수입니다.
    
* observe({})
    *  observeEvent({})와 eventReactive({})의 근간이 되는 함수로, input＄의 입력을 인지하는 역할을 합니다.


```R

```
