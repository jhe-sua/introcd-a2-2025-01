# introcd-a2-2025-01

*“Perfil de Artistas: Popularidade, Estilo e Engajamento nas Plataformas Digitais”*

---

### 🔎 Análise 1 – Índice de Popularidade Combinado

*Objetivo: Criar um KPI que sintetize em um único indicador o sucesso do artista em **streams (Spotify), **views, likes e comentários (YouTube)*.

* *KPI*: ÍndicePopularidade
* *DAX* (exemplo):

  dax
  ÍndicePopularidade =
    0.4 * NORMALIZE(SUM(Spotify[Stream])) +
    0.3 * NORMALIZE(SUM(YouTube[Views])) +
    0.2 * NORMALIZE(SUM(YouTube[Likes])) +
    0.1 * NORMALIZE(SUM(YouTube[Comments]))
  
* *Visual*: Gráfico de barras/ranking de artistas pelo índice.
* *Segmentadores*: Plataforma, tipo de lançamento, oficial/não oficial.

---

### 🔎 Análise 2 – Taxa de Engajamento

*Objetivo: Avaliar a **qualidade* do engajamento, não apenas o volume.

* *KPIs*:

  * LikesPorView = DIVIDE(SUM(YouTube[Likes]), SUM(YouTube[Views]))
  * CommentsPorStream = DIVIDE(SUM(YouTube[Comments]), SUM(Spotify[Stream]))
* *Visual*: Scatterplot “Índice de Popularidade x Taxa de Engajamento” e barras comparativas.
* *Filtros*: Apenas vídeos oficiais, por gênero musical (acoustic, danceable etc.).

---

### 🔎 Análise 3 – Estilo Musical vs. Sucesso

*Objetivo*: Relacionar atributos musicais dos artistas com sua performance nas plataformas.

* *Atributos*: valence, energy, danceability, speechiness, acousticness
* *Perguntas*:

  * Músicas felizes (valence > 0.5) têm mais streams/views?
  * Artistas dançantes geram mais likes?
* *Visual*: Matriz de calor ou dispersão multi-eixo (ex: valence x danceability x streams).
* *Segmentadores*: Faixas acústicas vs. eletrônicas, ao vivo vs. estúdio.

---

### 🔎 Análise 4 – Proporção de Conteúdo Oficial

*Objetivo*: Medir quanto do portfólio de cada artista é “oficial/licenciado” e como isso afeta o engajamento.

* *KPI*:

  dax
  ProporcaoOficial =
    DIVIDE(
      CALCULATE(COUNTROWS(YouTube), YouTube[official_video] = TRUE),
      COUNTROWS(YouTube)
    )
  
* *Visual*: Cartões por artista (% oficial) e gráfico de barras lado a lado (% oficial vs. média de views).
* *Filtros*: Canal, tipo de lançamento, plataforma.

---

### 🔎 Análise 5 – Comparação Multiplataforma

*Objetivo*: Identificar em qual plataforma cada artista “se destaca” e entender discrepâncias.

* *KPIs*:

  * DominioSpotify = SUM(Spotify[Stream]) - SUM(YouTube[Views])
  * DominioYouTube  = SUM(YouTube[Views]) - SUM(Spotify[Stream])
* *Visual*: Gráfico de radar com pontos para cada artista, mostrando streams vs. views.
* *Segmentadores*: Somente singles, somente faixas acústicas, por período de lançamento.

---

## 🧩 Estrutura do Dashboard

1. *Segmentadores Globais*

   * Artista
   * Plataforma (Spotify / YouTube)
   * Tipo de lançamento (single / álbum)
   * Estilo musical (alto/baixo valence, danceability, etc.)
2. *KPIs em Cartões*

   * Índice de Popularidade
   * Taxa de Engajamento (likes/view, comments/stream)
   * Proporção de Vídeos Oficiais
3. *Visualizações Interativas*

   * Ranking de artistas (barra)
   * Scatterplots e matrizes de calor
   * Gráfico de radar multiplataforma
4. *Design Coerente e Funcional*

   * Paleta de cores distinta por plataforma (ex: verde-Spotify, vermelho-YouTube)
   * Layout em grades, ícones discretos, legibilidade
   * Responsividade: filtros que atualizam todos os gráficos juntos

---

Esse tema garante que *cada membro* tenha uma análise *autônoma, mas que **converge* para o mesmo panorama de *“Perfil de Artistas”*, usando todas as ferramentas e recursos que você mencionou.

Pronto para começar a implementar? Posso ajudar com o *DAX completo, **esboço de layout* no Power BI, ou *roteiro da apresentação*!