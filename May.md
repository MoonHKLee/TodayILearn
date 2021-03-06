# TodayILearn
## 0410
인텔리 제이 서블릿 관련 이슈

인텔리제이에서 톰캣을 embeded해서 사용할 때 발생한 에러.

메이븐 pom.xml파일에서 의존성을 관리할 때 인텔리제이의 플러그인에 톰캣 관련 플러그인이 설치되어있다면

관련 플러그인 disable후 진행해야 할 필요가 있다.

메이븐에서 의존성을 추가하고 동시에 인텔리제이에서 플러그인이 설치가 되어있다면 두 개의 파일이 동시에 실행되어 서블릿 컨테이너가 제대로 생성되지 않는다.

이클립스에서 실행 하는 경우에도 마찬가지 일 것 같다. 요즘 기본적으로 ide에서 tomcat 플러그인을 지원해주기 때문에 의존성 제거를 해주거나 플러그인 disable 처리를 해주어야 할 것 같다.(확인 해보지는 않았으나 ide 문제일 줄 알고 인텔리제이->이클립스 변경해서 빌드 해보았으나 같은 문제가 발생하였음.

->의존성 추가 할 때 기존 플러그인과 중복되는 것이 있는지 체크를 해보는 것이 필요하다.

->에러메시지를 제대로 읽고 한줄 한줄 구글에 검색을 해보면 답이 나온다.

## 0509
스프링 
IOC: 의존관계 주입이라고도 하며, 어떤 객체가 사용하는 의존 객체를 직접 만들어서 사용하는게 아니라, 주입받아 사용하는 방법을 말한다.

예를들어서 클래스에 변수가 스스로 객체를 만들어서 인스턴스 내부에 등록되는것이 아니라 생성자를 이용해서 외부에서 인스턴스를 주입받아 인스턴스를 완성시키면 의존성을 주입받은 것이 된다. 이렇게 스스로 의존객체를 생성하는게 아니라 주입받아 사용을 하게 되는것을 보고 컨트롤의 역전 (Inversion of Control) 이라고 한다.

스프링이 없어도 장치만 마련되어 있다면 직접 의존관계를 주입할 수 있다. 그런데 이렇게 우리가 직접 만들지 않고 IOC컨테이너를 사용하는 이유는 개발자들의 논의와 노하우가 쌓여 최선의 사용법을 만들었기 때문이다. 빈들을 컨테이너로부터 가져와서 사용하는 설계가 아주 많은 개발자들의 의견을 바탕으로 만들어졌기 때문에 굉장히 안정적이다.

IOC의 핵심은 빈팩토리 인터페이스이다.

의존성 주입을 받고싶다면 먼저 빈이 되어야한다.

## 0510
스프링 어노테이션
@Component 
->어노테이션이 있는 클래스에 대하여 bean 인스턴스를 생성한다.

@Controller
-> 클라이언트로부터 전달되어진 데이터를 가공하기 위한 컨트롤러임을 명시하는 어노테이션
@RequestMapping을 통해서 경로 설정을 하게된다.

@Service
->Repository를 통해 데이터베이스에서 데이터를 가져온 후 컨트롤러에게 전달해 주는 클래스임을 명시.

@Repository
-> @Repository 는 해당 클래스가 데이터베이스에 접근하는 클래스임을 명시한다.

@Entity
->Spring data JPA를 사용할 시 데이터베이스에 테이블을 생성하거나 데이터를 가공하기 위한 클래스임을 명시.
@Entity 으로 클래스를 만들면 데이터베이스에 해당 클래스 이름으로 테이블을 만들고, 변수로 필드를 만든다.
이 또한 JPA를 통해 @Domain 클래스에서 사용되어지는  다양한 어노테이션이 존재하게 된다.

## 0519
안드로이드 코틀린 개발시 에러가 발생하면 일단 ?.를 찍어본다.

## 0521
파이썬 filter 함수 검색.

## 0530
JS--> __proto__를 사용한 Object간의 상속

자바에서는 클래스간의 extends를 통해서 상속을 가능하게 하지만
자바스트립트에서는 프로토 타입을 총해서 상속을 가능케 할 수 있다.

예를 들어서 

class Person{

  int age;
  
  String name;
  
  String job;
  
  Person(int age, String name, String job){
  
    this.age = age;
    
    this.name = name;
    
    this. job = job;
  }
}

class Student extends Person{
  int grade;
  String schoolName;
  
  Student(int age, String name, String job, int grade, String schoolName){
    super(age,name,job);
    this.grade = grade;
    this.schoolName = schoolName;
  }
}

이라는 클래스 형태를 통해서 상속을 진행했다면
자바스트립트에서는 

let superObj = {superVal:'super'};
let subObj = {subVal:'sub'};

subObj. __ proto __ = superObj;

라는 형태를 통해서 객체의 __proto__를 이용하여 객체간의 상속을 연결지을 수 있다.

물론  ES6 이후에 자바스트립트에도 class 개념을 도입하여 extends 를 사용하여 삭속을 진행 할 수 있기는 하다.
그 방법은 다음과 같다.

class Person{
    constructor(name, age, grade){
        this.name = name;
        this.age = age;
        this.grade = grade;

    }
    introduce() {
        return 'my name is \''+this.name+'\'. and i\'m \''+this.age+'\'. and i \'m \''+this.grade+'\'grade.';
    };
}

class PersonPlus extends Person{
    constructor(name,age,grade,iq){
        super(name,age,grade);
        this.iq=iq;
    }

    introducse() {
        return 'my name is \''+this.name+'\'. and i\'m \''+this.age+'\'. and i \'m \''+this.grade+'\'grade.';
    };

    getIq(){
        return this.age;
    }
}


하지만 __proto__ 를 사용하는 방법은 자바스크립트에서 정식으로 표준 지원하는 기능은 아니다.
물론 모든 브라우저들이 이 기능을 지원하기는 하지만 정식표준 기능은 따로있다.
바로 Object.create(superObject)를 사용하는 것이다.

예를 들어서

let superObj ={superVal:'super'}; 

subObj = Object.create(superObj); // subObj 가 superObj를 상속한다.
