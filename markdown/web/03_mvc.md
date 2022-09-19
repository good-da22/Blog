## Web Application Architecture - MVC

<br>

JSP를 이용하여 구성할 수 있는 Web Application Architecture는 크게 model1과 model2로 나뉜다.

JSP가 client의 요청에 대한 Logic 처리와 reponse page(view)에 대한 **처리를 모두** 하느냐

아니면 response page(view)에 대한 **처리만** 하는지가 가장 큰 차이점

Model2 구조는 MVC(Model - View - Controller) Pattern을 Web 개발에 도입한 구조를 말한다.

<br>

### Model 1 구조

<br>

model1 은 view와 logic을 JSP 페이지 하나에서 처리하는 구조를 말한다.

client로부터 요청이 들어오게 되면 JSP 페이지는 java beans나 별도의 service class를 이용하여 작업을 처리

결과를 client에 출력

간단한 page를 구성하기 위해 과거에 가장 많이 사용되었던 architecture

![model1](./../../img/inner%20ing/model1.png)

<br>

#### model 1 구조 장단점

<br>

**장점**

구조가 단순하며 직관적이기 때문에 배우기 쉽다.

개발 시간이 비교적 짧기 때문에 개발 비용이 감소

**단점**

출력을 위한 view(html) 코드와 로직 처리를 위한 java 코드가 섞여 있기 때문에 JSP 코드 자체가 복잡해진다.

JSP 코드에 Back-End(Developer)와 Front-End(Designer)가 혼재되기 때문에 분업이 힘들어 진다.

project 규모가 커지게 되면 코드가 복잡해 지므로 유지보수에 불리

확장성(신기술 도입, framework, ...)이 나쁘다.

<br>

### Model 2 구조

<br>

model2는 모든 처리를 JSP 페이지에서 하는 것이 아니라

client 요청에 대한 처리는 servlet

logic처리는 java class(Service, Dao, ...)

client에게 출력하는 response page(view)를 JSP가 담당

model 2 구조는 MVC(Model - View - Controller) pattern을 웹 개발에 도입한 구조이며 완전히 같은 형태를 보인다.

- **Model 2** : Service, Dao or Java beans
- **MVC Pattern** : Model
  
    Logic(Business & DB Logic)을 처리하는 모든 것

    controller로 부터 넘어온 data를 이용하여 이를 수행하고 그에 대한 결과를 다시 controller로 return

- **Model 2** : JSP
- **MVC Pattern** : View

    모든 화면 처리를 담당

    Client의 요청에 대한 결과 뿐 아니라 controller에 요청을 보내는 화면단도 jsp에서 처리

    Logic 처리를 위한 java code는 사라지고 결과 출력을 위한 code만 존재

- **Model 2** : Servlet
- **MVC Pattern** : controller

    Client의 요청을 분석하여 Logic 처리를 위한 Model 단을 호출

    return 받은 결과 data를 필요에 따라 request, session 등에 저장

    redirect 또는 forward 방식으로 jsp(view) page를 이용하여 출력


![model2](./../../img/inner%20ing/model2.png)

<br>

#### Model 2 장단점

<br>

Model 2 는 Model 1의 단점을 보완하기 위해 만들어 졌으나, 다루기 어렵다.

**장점**

출력을 위한 view(html) 코드와 로직 처리르 위한 java 코드 분리

JSP는 Model 1에 비해 코드가 복잡하지 않다.

화면단과 Logic단이 분리되어 분업에 용이

기능에 따라 code가 분리되어 유지보수 용이

확장성이 뛰어나다.

**단점**

구조가 복잡하여 초기 진입이 어렵다.

개발 시간 증가로 개발 비용 증가
