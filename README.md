# BEM (Block Element Modifier)

## Temiz Kod Anlayışı;

İyi yazılımcı güzel temiz kod yazan yazılımcıdır. Bir koda verilen önem kodun temizliğinden, yalınlığından anlaşılabildiği gibi yazan yazılımcımında işine verdiği değeri yansıtır aynı zamanda. Unutulmaması gereken nokta, yazılım bir sanattır ve sanatçısı yazılımcıdır :)

“Sonra asla demektir”
  
Bir kod yazılırken asla daha sonra temize çekerim diye başlanmamalı. Sonra temize çekme asla olmayacaktır. Çünkü;
Kod biriktikçe yönetilebilrliği azalacak, karmaşık ve anlamsız hale gelecektir.

##### Kod karmaşasının sonuçları;
> Takımların verimliliği düşer ve sıfıra yaklaşır. Verimlilik düştükçe de yöneticiler yapabildikleri tek şeyi yaparlar; verimliliği artırması umudu ile projeye daha çok insan kaynağı eklerler. Takımdaki herkes verimliliği artırmak için büyük baskı altındadır. Öyle ki verimliliği sıfıra daha da yaklaştıracak şekilde kod karmaşası yaratmaya devam ederler.

##### İyi kod nasıl kötü koda dönüşür;
> İyi bir kodun kötü koda dönüşmesinin bir çok nedeni vardır. En büyük nedenlarinden biride, maalesef profesyonel davranmamamız. Kodlarımızı günübirlik düşünüp, esnek, pratik düşünmüyoruz. Genelde günü kurtarmaya yönelik çalıştığımız için projeler ilerledikçe tıkanmakta ve kodun yönetimi zorlaşmaktadır.

#### Temiz kod için neler yapmalıyız?

"Temiz kod her zaman ona değer veren biri tarafından yazılmış gibi görünür."

- Bir kod yazılmadan önce parçalar ayrı ayrı düşünülmeli. Her bir parça sonradan kullanılabilir şekilde, mantıklı genel isimlendirmeler verilmeli.
- Gereksiz yorumlarda, kodlardan ve amaç dışında kullanımlardan uzak durulmalı.
- Program veya uygulamanın isterlerine göre uygun ölçekte pozitif parça ve parçacıklardan oluşmalı.
- İlişkili teknoloji ve dillere uygun, rahat yorumlanıp, okunulabilir bir yapıyla proje iskeleti oluşturulup geliştirmeye hazır olmalı.
- İş ortamında iletişim iyi düzeyde tutulup, gerekli durumlarda proje ile ilgili takım içi iletişimden çekinmemeli. 

Unutulmaması gerekir, temiz kod arayışında olmak iyi yazılımcı olmak için atılacak en büyük adım olur.


## BEM Nedir ?

BEM (Block Element Modifier) bir css metadolojisidir. Yandex Tarafından geliştirilmiş, bir stil adlandırma kuralıdır.

BEM ile doğru, stabil ve belli bir standart isimlendirmeler amaçlanmaktadır. Kodun okunulabilir olması için oldukça önemli bir yer almaktadır.

#### Peki nedir bu Block Element Modifier ;
#### Block;
> Genelde birden fazla elementi kapsayan büyük yapılardır. Bloklar kendi içlerinde birden fazla item'ı grup olarak içinde barındırır. Kendi içinde blocklar bulundurabilirler. Oluşturduğumuz componentler, widgetlar veya global tanımlı her bir anlamlı parçalar birer block parçası olabilir ve block olarak tanımlanabilir.

 ![Alt text](https://miro.medium.com/max/1257/1*eFlkVoLUdAy8eSJXPBBG6Q.png?raw=true "Title")
 
Yukarıdaki Twitter home page örneğinde, sayfanın mantıklı bloklara ayrılış biçimi kırmısı borderlar ile görünmektedir. Her bir parça bir BEM bloğunu temsil etektedir. Örnekteki bloklar Header, side-left, side-right, ve main gibi isimlendirilebilir.

![Alt text](https://miro.medium.com/max/1206/1*xUMPgcFYsL53DEK7CgdOsQ.png?raw=true "Title")

Yukardaki görüntüde header bloğununda kendi içinde üç ara bloğa bölündüünü görebiliriz.
 
  ![Alt text](https://miro.medium.com/max/140/1*ZApq-kqz0s-G7xmn2cu0Zg.png?raw=false "Title")
   .header bloğu içindeki .logo bloğu
   
    
Genel olarak örneklere Header bloğu ile devam edeceğiz.

```
  <header class="header">
      ///HTML5 semantic element'i olan header'a ".header" class'ı verilerek bloğumuzu oluşturmuş olduk.
  </header>
  
```

```
<!-- HTML -->
  <header class="header">
    <nav class="nav">
      ///Burda Blok içinde blok ypmış olduk.
    </nav>
  </header>
  
<!-- HTML -->

.nav {
  ....
}


```

#### Element
> Element'ler temelde block'lar içinde olan ` blok elemanlarıdır `. 

  ![Alt text](https://miro.medium.com/max/378/1*4htCS_T0z8RAIQzl68qlKQ.png?raw=false "Title")
    .header bloğu içindeki .search bloğu
    
```
<div class="block">
  <div class="block__element">
    //content
  </div>
</div>

```
Search Bloğu ;

```
<!-- HTML -->
<header class="header">
  <div class="search">
     <input class="search__input" type="text" name="search" placeholder="Search Twitter">
     <img class="search__profile-img" src="../../profile.png">
     <button class="search__button" type="button">Tweet</button>
  </div>
</header>
  
<!-- CSS (less veya sass ile birlikte) -->

.search {
  ...
  
  &__input {
    ...
  }
  &__profile--img {
    ...
  }
  &__button {
    ...
  }
}
   
```


### Modifier
 Block elemanına ek stiller kullanmak için oluşturulur.
 
  ![Alt text](https://miro.medium.com/max/378/1*ynf3eybGhZXs-1F-l_3AdQ.png?raw=false "Title")
    .header bloğu içindeki .search bloğu
 
 ```
 <!-- HTML -->
 <header class="header">
  <div class="search">
     <input class="search__input" type="text" name="search" placeholder="Search Twitter">
     <img class="search__profile-img" src="../../profile.png">
     <button class="search__button search__button--error" type="button">Tweet</button>
  </div>
</header>

<!-- CSS (less veya sass ile birlikte) -->

.search {
  ...
  
  &__input {
    ...
    
    &--error {
      ...
    }
  }
}
   
 
 ```
 
 
#### BEM Örnek UI Örneği;

![Alt text](image/code-rev-1.jpg?raw=false "Title")

```

<div class="hero">
  <header class="header">
    <div class="container">
      <nav class="nav">
        <div class="nav__item">
          <a href="#" class="nav__item--link">
            .....
          </a>
        </div>	
        ....
      </nav>
    </div>
  </header>

  <div class="hero__content">
      <div class="logo">
        <img src="...." class="logo__img">
      </div>

      <div class="search">
        <form class="search__form">
          <input class="search__input" ..... >
          <button class="search__button" .... > Search </button>
        </form>
      </div>

      <div class="auth">
        <form class="auth__form">
          <input class="auth__input" .... placeholder=".....">
          <input class="auth__input" .... placeholder=".....">
          <button class="auth__button" ..... > Sign İn </button>
        </form>
      </div>
    </div>
  </div>
</div>
  
```

### Temel Adlandırma Kuralları 

* #id selector kullanımı min seviyede olmalı. id selector kullanılacaksa sadece js etkileşim için kullanılmalı ve css verilmemeli. Unutulmamalıdır ki id selector çok güçlü bir seçici. 

* Element adı block adından çift alt tire ( __ ) ile ayrılmalı. örn: " .block__element " 
* Modifierler element veya block'tan çift tire ( -- ) ile ayrılmalı. örn: " .block__element--modifier // .block--modifier"

Örn;

```
<div class="block">
  <div class="block__element block--modifier">
    . . .
  </div>
</block>

```

Yanlış Kullanım;

```
<div class="block">
  <div class="block__element">
    <div class="block__element__container">
      . . .
    </div>
  </div>
</block>

```
Doğru Kullanım;

```
<div class="block">
  <div class="block__element">
    <div class="block__container">
      . . .
    </div>
  </div>
</block>

```


bonus olarak;

Örn-1;
```
.kisi__el
.kisi__bacak
.kisi--erkek
.kisi--erkek__el
.kisi--erkek__el--sol
.kisi--erkek__el--sag
.kisi--erkek__bacak
.kisi--erkek__bacak--sol
.kisi--erkek__bacak--sag
.kisi--kadin
.kisi--kadin__hand
.kisi--kadin__hand--sol
.kisi--kadin__hand--sag
.kisi--kadin__bacak
.kisi--kadin__bacak--sol
.kisi--kadin__bacak--sag

```

Örn-2;

![Alt text](https://miro.medium.com/max/1080/0*E9SgMh-FsWFBmG09.png?raw=false "Title")


### BEM kullanmanın avantajları;

* Kodun daha okunabir, yorumlanabilir olmasını sağlıyor.
* Kodun esnek olmasını bu sayede kod tekrarını engelliyor.
* Sass ve Less gibi css pre-processor’lar için de BEM üretmek oldukça kolay.
* İç içe css seçicilerinden oluştuğu için hangi elementin hangi bloğa ait olduğu ve amacı çabuk anlaşılır. Ufak html isim değişiklerinde hemen güncelleme uygulanabilir olmakta.

## OOCSS (Object Oriented CSS)

BEM gibi bir css metadolojisidir.
> OOCSS'in odak noktası, sayfa öğelerinde tekrar edilen durumları nesne olarak ele almak ve gerektiğinde kullanmaktır.

##### OOCSS'nin referans aldığı noktalar;

1 ) Düzen stillerinin (width, height, padding, margin , position) ve tasarım stillerinin(border, color, font, background) birbirinden ayrılması demektir.

Örn;
```
/* kötü kullanım */
.box-1{
   width: 100px;
   height: 100x;
   border: 1px solid #ccc;
   border-radius: 5px;
   color: #ccc;
}
.box-2{
   width: 200px;
   height: 200x;
   border: 1px solid #ccc;
   border-radius: 5px;
   color: #ccc;
}
/* doğru kullanım */
.box-1{
   width: 100px;
   height: 100x;
}
.box-2{
   width: 200px;
   height: 200x;
}
.box-border{
   border: 1px solid #ccc;
   border-radius: 5px;
   color: #ccc;
}
<!-- HTML -->
<div class=”box-1 box-border”> Lorem ipsum </div>
<div class=”box-2 box-border”> Lorem ipsum </div>


```

2 ) Child-selector min seviyede kullanmak;

```
<!-- HTML  -->
<div class=”sidebar”>
   <h2 class=”sidebar-title”>
     . . . 
  </h2>
      . . .
      . . .
</div>


/* Doğru kullanım */

.sidebar{
   . . .
   
   &-title{
     . . .
   }
}

/* Yanlış kullanım */
.sidebar{
   . . .
}
.sidebar h2{
   . . .
}

```

### OOCSS kullanmanın avantajları;
* Kod tekrarını azaltıp css dosyamızın şişmesini engeller. Kod tekrarı olmadığı için sitenin performansını olumlu yönde etkiler.
* Esnek, Korunabilir ve ölçeklenebilir olduğu için yeniden kullanılabilirliği sağlar.
* Kolay okunabilirliği sağlar. Bu sayede kodun geliştirmesi rahat olur.
* OOCSS’te parçalar CSS’de kodlanıp ve HTML’de genişletiliyor.

### Metodolojilerde sonuç olarak;




Genele bakacak olursak, Temiz kod yazma, kötü kod nasıl oluşur, ve temiz kod yazmak için nasıl bir metodoloji yolu izlenmeli hakkında bilgi paylaşımımız oldu. Bug ve revizeleri azaltmanın bir yoluda kodu doğru ve mantıklı sıralar halinde yazmaktır. BEM ve OOCSS gibi css stil metodolojileri kodu doğru uygulamayı, belli bir global standartları kullanmayı hedefler. Böylece kodun okunabilirliği, yazılabilirliği, bakım ve geliştirmeleri çok rahat bir şekilde yapılmasını sağlar. 



### Temelel düzeyde style uygulama önerilerim;

Gördüğüm birkaç yanlış style uygulama biçimleri. Bu yazım biçimleri yukarda bahsı geçen kurallara ters düşmektedir.
```
.multi-image-text{
  background-color: white;
  &__title{
  font-size: 44px;
  line-height: 0.68;
  letter-spacing: 1.76px;
  text-align: center;
  color: #1d1d1d;
  position: relative;
  margin-bottom: 33px;
  
  &.multi-image-text__title--border{
    &::after{
      left: 50%;
      position: absolute;
      content: '';
      height: 1px;
      width: 180px;
      bottom: -12px;
      background-color: #bfbfbf;
      transform: translateX(-50%);
    }
  }
}
  &__description{
  font-size: 16px;
  line-height: 1.88;
  letter-spacing: 1.28px;
  text-align: center;
  color: #7a7a7a;
  margin-bottom: 25px;
  }
}
.multi-image-slider{
  background-color: #f5f5f5;

  .icon-sol{
    position: absolute;
    top: 0;
    bottom: 0;
    font-size: 40px;
    color: #7a7a7a;
    left: -26px;
    background: transparent;
}

----------------------

.col-sm-6:nth-child(2) {
  padding-bottom: 40px;
  position: absolute;
  bottom: 2%;
  left: 0;
}

.col-sm-7 {
  padding: 30px 30px 30px 100px;
}


------------------------

div {
  font-size: 16px;
  line-height: 1.63;
  letter-spacing: 0.96px;
  color: #7a7a7a;
  text-align: center;
}

-----------------------

.js-prev-slide, .js-next-slide {
  cursor: pointer;
  position: absolute;
  top: 25%;
  color: #bfbfbf;
  transition: 0.6s ease;
  font-size: 40px;
  z-index: 999;
}

.js-next-slide {
  right: -15px;
}

.js-prev-slide {
  left: -15px;
}

----------------------

a{
  transition: 0.2s ease;
  display: block;
  border: 1px solid #bfbfbf;
  height: 50px;
  padding: 6px 12px;
  position: relative;

  i{
    position: absolute;
    left: 8px;
    text-align: center;
    width: 32px;
    font-size: 20px;
    line-height: 36px;
  }

  span{
    display: block;
    letter-spacing: 1.1px;
    color: #1d1d1d;
    font-size: 14px;
    padding-left: 30px;
    line-height: 19px;
    text-transform: uppercase;
  }
}

```

### Responsive uygulama Önerilerim;

![Alt text](image/code-rev-1.jpg?raw=false "Title")

