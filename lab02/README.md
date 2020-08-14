# Modelo para Apresentação do Lab02 - Data Flow & Mensagens

Estrutura de pastas:

~~~
├── README.md  <- arquivo apresentando a tarefa
│
└── notebook   <- arquivo do notebook
~~~

## Tarefa sobre catálogo de componentes
LINK: https://github.com/assouza19/inf331/blob/master/lab02/notebook/components-01-catalog.ipynb

## Tarefa Web Components 1

~~~html
<dcc-trigger label="Mundo" action="send/world" value="Esta é uma notícia sobre POLÍTICA no mundo.">
</dcc-trigger>

<dcc-trigger label="Brasil P" action="send/brazil_p" value="Esta é uma notícia sobre POLÍTICA no Brasil.">
</dcc-trigger>

<dcc-trigger label="Brasil E" action="send/sport" value="Esta é uma notícia sobre ESPORTES no Brasil.">
</dcc-trigger>

<dcc-trigger label="Bahia" action="send/sport_ba" value="Esta é uma notícia sobre ESPORTES na Bahia.">
</dcc-trigger>


<dcc-lively-talk duration="0s" character="doctor" speech="Notícias de Política: ">
  <subscribe-dcc topic="send/world"></subscribe-dcc>
  <subscribe-dcc topic="send/brazil_p"></subscribe-dcc>
</dcc-lively-talk>

<dcc-lively-talk duration="0s" character="nurse" speech="Notícias do Brasil: ">
  <subscribe-dcc topic="send/brazil_p"></subscribe-dcc>
  <subscribe-dcc topic="send/sport_ba"></subscribe-dcc>
  <subscribe-dcc topic="send/sport"></subscribe-dcc>
</dcc-lively-talk>

<dcc-lively-talk duration="0s" character="patient" speech="Todas as notícias: ">
  <subscribe-dcc topic="send/world"></subscribe-dcc>
  <subscribe-dcc topic="send/brazil_p"></subscribe-dcc>
  <subscribe-dcc topic="send/sport_ba"></subscribe-dcc>
  <subscribe-dcc topic="send/sport"></subscribe-dcc>
</dcc-lively-talk>
~~~

## Tarefa Web Components 2

~~~html
<dcc-trigger label="Next News of Science" action="next/rss">
</dcc-trigger>

<dcc-trigger label="Next News of Design" action="next/rss_design">
</dcc-trigger>

<dcc-rss publish="rss/design" source="https://www.wired.com/category/design/feed">
  <subscribe-dcc topic="next/rss_design" role="step"></subscribe-dcc>
</dcc-rss>

<dcc-rss publish="rss/science" source="https://www.wired.com/category/science/feed">
  <subscribe-dcc topic="next/rss" role="step"></subscribe-dcc>
</dcc-rss>

<dcc-aggregator publish="aggregate/science" quantity="3">
  <subscribe-dcc topic="rss/science"></subscribe-dcc>
</dcc-aggregator>

<dcc-lively-talk id="doctor"
                 duration="0s"
                 character="nurse"
                 speech="News of Science">
  <subscribe-dcc topic="rss/science"></subscribe-dcc>
</dcc-lively-talk>

<dcc-lively-talk id="doctor"
                 duration="0s"
                 character="doctor"
                 speech="Aggregated news of science">
  <subscribe-dcc topic="aggregate/science"></subscribe-dcc>
</dcc-lively-talk>

<dcc-lively-talk id="doctor"
                 duration="0s"
                 character="patient"
                 speech="News of Design">
  <subscribe-dcc topic="rss/design"></subscribe-dcc>
</dcc-lively-talk>
~~~
