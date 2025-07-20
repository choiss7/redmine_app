목표: "작업 내역"처럼 리스트 스타일로 바꾸기
_news.html.erb를 수정하면 됩니다. 예를 들어 다음과 같이 바꾸면 됩니다:

📄 app/views/news/_news.html.erb 예시 수정:
erb
복사
편집
<li>
  <%= link_to h(news.title), :controller => 'news', :action => 'show', :id => news %>
  - <span class="author">
    <%= authoring news.created_on, news.author %>
  </span>
</li>
그리고 index.html.erb에서 render 호출을 아래와 같이 <ul>로 감싸줍니다:

📄 변경: index.html.erb 내 news 영역
기존:

erb
복사
편집
<div class="news box">
<h3><%=l(:label_news_latest)%></h3>
  <%= render :partial => 'news/news', :collection => @news %>
  <%= link_to l(:label_news_view_all), :controller => 'news' %>
</div>
변경 후:

erb
복사
편집
<div class="news box">
  <h3><%= l(:label_news_latest) %></h3>
  <ul class="news-list">
    <%= render :partial => 'news/news', :collection => @news %>
  </ul>
  <%= link_to l(:label_news_view_all), :controller => 'news' %>
</div>
🎨 CSS 예시 (선택)
css
복사
편집
.news-list li {
  margin-bottom: 6px;
  line-height: 1.4em;
}
이렇게 하면 뉴스가 다음처럼 보이게 됩니다:

python-repl
복사
편집
• 레드마인 AI 챗봇 오픈 - 최 성순, 6달 전
• EXAONE_v3.5 오픈과 AWS 마켓 플레이스 판매 - 최 성순, 7달 전
...
📌 요약
파일 경로	수정 내용
views/news/_news.html.erb	뉴스 항목을 <li> 형식으로 출력
views/welcome/index.html.erb	뉴스 전체를 <ul>로 감싸기
선택: application.css 등	리스트 스타일 조정 (선택 사항)

