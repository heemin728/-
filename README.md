
---

# GFM ( Github Flavored Markdown)
# 컴퓨터학부 20203083 강희민

- 확장된 부분만 설명

---

<br><br>
## Leaf Blocks - Tables (표)

- 열과 행으로 이루어진 정렬
- 셀은 pipe(|)로 구분 - 명료성을 위해 앞뒤로 pipe를 추가할 수 있음
- 열을 구분하는 문자로 hyphens(-)만 사용, 앞 뒤로 colon(:)을 이용해 좌우/가운데 정렬 표기
- header row 아래는 열을 구분하는 문자 (-)가 반드시 있어야 함

      | number | name |
      :-: | -----------:
      1 | apple

  | number | name |
  :-: | -----------:
  1 | apple
<br>

- pipe(|)를 표기하기 위해 이스케이프 문자(\) 사용    
    
      | pipe\|character  |
      | ------ |
      | gfm `\|` markdown |
      | github **\|** markup |
     
  | pipe\|chharacter  |
  | ------ |
  | gfm `\|` markdown |
  | github **\|** markup |
<br>

- 빈 줄 혹은 다른 블록을 만나면 표 중단

      | year | grade |
      | --- | --- |
      | 2020 | 1 |
      | 2021 | 2 |
      > bar
      
  | year | grade |
  | --- | --- |
  | 2020 | 1 |
  | 2021 | 2 |
  > bar
<br>

- header row의 셀보다 적은 셀이 입력되면 빈 셀 생성/ 많은 셀이 입력되면 무시 

      | number | name |
      | --- | --- |
      | 0 |
      | 1 | Kim | Lee |

  | number | name |
  | --- | --- |
  | 0 |
  | 1 | Kim | Lee |
<br>

- body가 입력되지 않으면, header만 출력

      | abc | def |
      | --- | --- |
           
  | abc | def |
  | --- | --- |
<br><br>

## Container Blocks - Task list items

- GFM은 task list 확장을 지원함
- task list item marker로 시작하며, **공백이 필요**함
- [ character ] - html의 <input type="checkbox"> 와 같음
- [ ] 사이가 비면 체크되지 않음
- [ ]에 'x' 또는 'X' 가 입력되면 체크됨
- 체크박스 요소가 어떻게 상호작용 하는지는 정의하지 않음
- nested 될 수 있음

      - [x] markup 
        - [ ] html
        - [x] markdown
      - [ ] programming

  - [x] markup
    - [ ] html
    - [x] markdown
  - [ ] programming

<br><br>
## Inlines - strikethrough
- 추가적인 강조 타입 사용 (취소선) 
- tildes(~)로 둘러쌓임

      ~~2020~~ It's 2021!
   ~~2020~~ It's 2021!

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
    - underscore(_) 는 도메인의 마지막 두 부분에 존재할 수 있음
 - http는 자동으로 삽입됨
 
             www.ssu.ac.kr/
 
 www.ssu.ac.kr/
  
 - 링크의 끝에 오는 후행 구두점 ( ?, !, ., ,, :, \*, _, ~) 는 링크의 일부로 보지 않음 
 - autolink가 ')'로 끝날 경우, '(' 의 개수보다 많은 경우 autolink에서 제외함 
 - ')'가 링크의 중간에 존재하는 경우 적용되지 않음

        www.google.com/search?q=Markup+(business)

        www.google.com/search?q=Markup+(business)))

        (www.google.com/search?q=Markup+(business))

        (www.google.com/search?q=Markup+(business)
    
   www.google.com/search?q=Markup+(business)

  www.google.com/search?q=Markup+(business)))

  (www.google.com/search?q=Markup+(business))

  (www.google.com/search?q=Markup+(business)
  
  - 맨 끝에 세미콜론 (;) 이 올 경우, 앞서 &과 알파벳이 존재하면(entity reference) autolink에 포함

        www.google.com/search?q=commonmark&hl=en

        www.google.com/search?q=commonmark&hl;

  www.google.com/search?q=commonmark&hl=en

  www.google.com/search?q=commonmark&hl;
  
  - '<' 가 올 경우 즉시 링크를 끝냄
  
        https://myclass.ssu.ac.kr/log<in.php
  
    https://myclass.ssu.ac.kr/log<in.php
    
 - email autolink는 이메일 주소가 인정되면 가능
    - 하나 이상의 글자가 알파벳, **.** , **+**, **-** , **_** 인 경우
    - @ 글자가 존재하는 경우 
    - 하나 이상의 알파벳, **-**,**_** 은 peroids(.)에 의해 구분됨
    - 적어도 하나의 period(.)가 있어야 하며, 마지막 문자가 _ 또는 -일 수 없음
    - +은 @의 전에는 사용 가능, 후에는 불가
 - scheme  `mailto:` 는 생성된 링크에 자동으로 추가됨
 - **+**는 **@** 의 이전에는 사용 가능하지만, 이후에는 사용할 수 없음
 - **.**, **-**, **_** 는 **@** 의 앞 뒤에 모두 사용할 수 있음
      - **.** 만 이메일 주소의 끝에 사용되며, 주소의 일부로 생각하지 않음

            a.b-c_d@a.b
            a.b-c_d@a.b.
            a.b-c_d@a.b-
            a.b-c_d@a.b_

      a.b-c_d@a.b
      a.b-c_d@a.b.
      a.b-c_d@a.b-
      a.b-c_d@a.b_

<br><br>

## Inlines - Disallowed Raw HTML 

- GFM은 tagfilter확장을 지원함
- Filtering 은 <를 &lt 로 대체함 - HTML이 해석되는 방법을 바꿈
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
  
- 다른 HTML 태그는 그대로 사용

        <strong> <title> <style> <em>

        <blockquote>
          <xmp> is disallowed.  <XMP> is also disallowed.
        </blockquote>
    
    
<strong> <title> <style> <em>

<blockquote>
  <xmp> is disallowed.  <XMP> is also disallowed.
</blockquote>


## Emojis

- type :EMOJICODE: 

https://github.com/ikatyang/emoji-cheat-sheet/blob/master/README.md#smileys--emotion
