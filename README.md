# GFM ( Github Flavored Markdown)

- 확장된 부분만 설명

<br><br>
## Leaf Blocks - Tables (표)

- 열과 행으로 이루어진 정렬
- 셀은 pipe(|)로 구분 - 명료성을 위해 앞뒤로 pipe를 추가할 수 있음
- 열을 구분하는 문자로 hyphens(-)만 사용, 앞 뒤로 colon(:)을 이용해 좌우/가운데 정렬 표기
- header row 아래는 열을 구분하는 문자 (-)가 반드시 있어야 함

      | abc | defghi |
      :-: | -----------:
      bar | baz

  | abc | defghi |
  :-: | -----------:
  bar | baz
<br>

- pipe(|)를 표기하기 위해 이스케이프 문자(\) 사용    
    
      | f\|oo  |
      | ------ |
      | b `\|` az |
      | b **\|** im |
     
  | f\|oo  |
  | ------ |
  | b `\|` az |
  | b **\|** im |
<br>

- 빈 줄 혹은 다른 블록을 만나면 표 중단

      | abc | def |
      | --- | --- |
      | bar | baz |
      > bar
      
  | abc | def |
  | --- | --- |
  | bar | baz |
  > bar
<br>

- header row의 셀보다 적은 셀이 입력되면 빈 셀 생성/ 많은 셀이 입력되면 무시 

      | abc | def |
      | --- | --- |
      | bar |
      | bar | baz | boo |

  | abc | def |
  | --- | --- |
  | bar |
  | bar | baz | boo |
<br>

- body가 입력되지 않으면, header만 출력

      | abc | def |
      | --- | --- |
           
  | abc | def |
  | --- | --- |
<br><br>

## Container Blocks - Task list items
- task list 확장 가능
- [ character ] - html의 <input type="checkbox"> 와 같음
- [] 사이가 비면 체크표시 x, 문자가 입력되면 체크표시
- 체크박스 요소가 어떻게 상호작용 하는지는 정의하지 않음
- nest 할 수 있음

      - [x] foo
        - [ ] bar
        - [x] baz
      - [ ] bim

  - [x] foo
    - [ ] bar
    - [x] baz
  - [ ] bim

<br><br>
## Inlines - strikethrough
- 추가적인 강조 타입 사용 (취소선) 
- tildes(~)로 둘러쌓임

      ~~Hi~~ Hello, world!
  ~~Hi~~ Hello, world!

- 단락이 새로 생성되면 강조 멈춤

      This ~~has a

      new paragraph~~.

    This ~~has a

    new paragraph~~.
    
 <br><br>
 
 ## Inlines - Autolinks
 - 범위를 정하기 위한 <, > 이 필요하지 않음
 - 라인의 처음, 공백 이후, 또는 범위를 정하기 위한 \*, ~, _, ( 이후에 올 수 있음
 - autolink는 ' www. '과 이후의 valid domain이 오면 인식됨
    - valid domain은 period(.)에 의해 구분되는 알파벳, hyphens(-), underscores(_) 로 구성됨
    - 최소 하나 이상의 period(.)이 필요
 - http는 자동으로 삽입됨
 - 링크에 끝에 오는 후행 구두점 ( ?, !, ., ,, :, \*, _, ~) 는 링크의 일부로 보지 않음 
 - autolink가 ')'로 끝날 경우, '(' 의 개수보다 많은 경우 autolink에서 제외함 

        www.google.com/search?q=Markup+(business)

        www.google.com/search?q=Markup+(business)))

        (www.google.com/search?q=Markup+(business))

        (www.google.com/search?q=Markup+(business)
    
   www.google.com/search?q=Markup+(business)

  www.google.com/search?q=Markup+(business)))

  (www.google.com/search?q=Markup+(business))

  (www.google.com/search?q=Markup+(business)
  
  - 맨 끝에 세미콜론 (;) 이 올 경우, 앞서 &과 알파벳이 존재하면 autolink에 포함

        www.google.com/search?q=commonmark&hl=en

        www.google.com/search?q=commonmark&hl;

  www.google.com/search?q=commonmark&hl=en

  www.google.com/search?q=commonmark&hl;
  
  - '<' 가 올 경우 즉시 링크를 끝냄
  
        www.commonmark.org/he<lp
  
    www.commonmark.org/he<lp
    
 - email autolink는 이메일 주소가 인정되면 가능
    - 하나 이상의 글자가 알파벳, . , +, - , _ 인 경우
    - @ 글자가 존재하는 경우 
    - 적어도 하나의 period(.)가 있어야 하며, 마지막 문자가 _ 또는 -일 수 없음
    - +은 @의 전에는 사용 가능, 후에는 불가

<br><br>

## Inlines - Disallowed Raw HTML 

- GFM은 tagfilter확장을 지원함
- 다음 9가지 html tag는 filtering 됨
  - <title>
  - <textarea>
  - <style>
  - <xmp>
  - <iframe>
  - <noembed>
  - <noframes>
  - <script>
  - <plaintext>

        <strong> <title> <style> <em>

        <blockquote>
          <xmp> is disallowed.  <XMP> is also disallowed.
        </blockquote>
    
    
<strong> <title> <style> <em>

<blockquote>
  <xmp> is disallowed.  <XMP> is also disallowed.
</blockquote>
