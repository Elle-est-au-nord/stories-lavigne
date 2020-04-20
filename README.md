# Letting go of early 2000's Avril Lavigne

This is me (hey! I'm Éléonore Mayola) coming to you with a crucial investigation into what happened to Avril Lavigne in the early 2000's.

This announcement might surprise you if, unlike me, you haven't wandered down the comments under one of her early YouTube video. That's where I discovered a specific group of Lavigne fans are convinced she passed away in 2003 and was replaced by a lookalike [1,2].

It is a fact that Avril Lavigne changed in both her music and style, but who doesn't change over time. The explanation being that transformation is very unlikely to be so dramatic, but then what happened?
While it is tricky to account for her personal /internal evolution, some of her musical influences (such as her support band and producing partners) can be looked at to find a correlation with her visible transformation (music and style).

<img src="img/album_covers.png" title="Lavigne studio album covers" />
[8]

Avril Lavigne's albums popularity decreased especially after the 3rd album. This third album seems different in its content (more energy, more speechiness) and has songs viewed as part of a style called "Bubblegum Pop" and the first time Avril Lavigne produces songs. It was made after she left Arista Records, and after the biggest musicians turnover in her backing band. While her style (hair, clothes) started to change between the two first albums (released in 2002 and 2004), which is consistent with her leaving teenagehood, her biggest musical change happened on the third album (2007). This change in both style and music has lost her a part of her fans. And it could obviously not be explained by the artist being replaced in 2003.


```python
import pandas as pd
import altair as alt
alt.renderers.enable('notebook')
```




    RendererRegistry.enable('notebook')



## Avril Lavigne studio albums data
[3, 4, 5]


```python
al_albums = [
    {"name": "Let Go", "year": 2002, "genre": ["Alternative rock","Pop punk"], "global_sales": 16220000, 
     "billboard200_debut": 2, "label": ["Arista Records"], 
     "producers": ["L.A. Reid", "The Matrix", "Clif Magness", "Curt Frasca", "Peter Zizzo"]},
    {"name": "Under My Skin", "year": 2004, "genre": ["Alternative rock","Pop punk"], "global_sales": 8020000, 
     "billboard200_debut": 1, "label": ["Arista Records", "RCA Records"], 
     "producers": ["Raine Maida", "Don Gilmore", "Butch Walker"]},
    {"name": "The Best Damn Thing", "year": 2007, "genre": ["Bubblegum pop","Pop punk"], "global_sales": 5660000, 
     "billboard200_debut": 1, "label": ["RCA Records"], 
     "producers": ["Avril Lavigne", "Deryck Whibley", "Butch Walker", "Rob Cavallo", "Dr. Luke", 
                  "The Submarines", "Jesse Welch", "Steven Wolf"]},
    {"name": "Goodbye Lullaby", "year": 2011, "genre": ["Pop rock"], "global_sales": 1650000, 
     "billboard200_debut": 4, "label": ["RCA Records"], 
     "producers": ["Avril Lavigne", "Deryck Whibley", "Butch Walker", "Max Martin", "Shellback"]},
    {"name": "Avril Lavigne", "year": 2013, "genre": ["Pop", "Pop rock"], "global_sales": 740000, 
     "billboard200_debut": 5, "label": ["Epic Records"], 
     "producers": ["Avril Lavigne", "L.A. Reid", "Martin Johnson", "Peter Svensson", 
                  "David Hodges", "Matt Squire", "Chad Kroeger"]},
    {"name": "Head Above Water", "year": 2019, "genre": ["Pop rock"], "global_sales": None, 
     "billboard200_debut": 13, "label": ["BMG"], 
     "producers": ["Avril Lavigne", "Stephan Moccio", "Chris Baseford", "Johan Carlsson", 
                   "Lauren Christy", "Ryan Cabrera", "Chad Kroeger"]}
]
```


```python
df_albums = pd.DataFrame(al_albums)
```


```python
df_albums
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>year</th>
      <th>genre</th>
      <th>global_sales</th>
      <th>billboard200_debut</th>
      <th>label</th>
      <th>producers</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>Let Go</td>
      <td>2002</td>
      <td>[Alternative rock, Pop punk]</td>
      <td>16220000.0</td>
      <td>2</td>
      <td>[Arista Records]</td>
      <td>[L.A. Reid, The Matrix, Clif Magness, Curt Fra...</td>
    </tr>
    <tr>
      <td>1</td>
      <td>Under My Skin</td>
      <td>2004</td>
      <td>[Alternative rock, Pop punk]</td>
      <td>8020000.0</td>
      <td>1</td>
      <td>[Arista Records, RCA Records]</td>
      <td>[Raine Maida, Don Gilmore, Butch Walker]</td>
    </tr>
    <tr>
      <td>2</td>
      <td>The Best Damn Thing</td>
      <td>2007</td>
      <td>[Bubblegum pop, Pop punk]</td>
      <td>5660000.0</td>
      <td>1</td>
      <td>[RCA Records]</td>
      <td>[Avril Lavigne, Deryck Whibley, Butch Walker, ...</td>
    </tr>
    <tr>
      <td>3</td>
      <td>Goodbye Lullaby</td>
      <td>2011</td>
      <td>[Pop rock]</td>
      <td>1650000.0</td>
      <td>4</td>
      <td>[RCA Records]</td>
      <td>[Avril Lavigne, Deryck Whibley, Butch Walker, ...</td>
    </tr>
    <tr>
      <td>4</td>
      <td>Avril Lavigne</td>
      <td>2013</td>
      <td>[Pop, Pop rock]</td>
      <td>740000.0</td>
      <td>5</td>
      <td>[Epic Records]</td>
      <td>[Avril Lavigne, L.A. Reid, Martin Johnson, Pet...</td>
    </tr>
    <tr>
      <td>5</td>
      <td>Head Above Water</td>
      <td>2019</td>
      <td>[Pop rock]</td>
      <td>NaN</td>
      <td>13</td>
      <td>[BMG]</td>
      <td>[Avril Lavigne, Stephan Moccio, Chris Baseford...</td>
    </tr>
  </tbody>
</table>
</div>




```python
#df_albums.to_csv("al_albums_data.csv")
```

### Albums sales and debut in US charts


```python
chart1 = alt.Chart(df_albums, width=300, height=200).mark_point(size=100, filled=True, opacity=0.8).encode(
    alt.X('year',
        scale=alt.Scale(domain=(1999, 2019))
    ),
    y='global_sales:Q',
    color=alt.Color('name', sort=['year'])
)

chart2 = alt.Chart(df_albums, width=300, height=200).mark_bar(size=20, opacity=0.8).encode(
    x='year:O',
    y=alt.Y('billboard200_debut:Q', 
           scale=alt.Scale(domain=(0, 15))),
    color=alt.Color('name', sort=['year'])
)

chart1 | chart2
```


    <vega.vegalite.VegaLite at 0x7f31095e65c0>





    




![png](output_11_2.png)



```python
# chart1.save('plots/chart1.json')
# chart2.save('plots/chart2.json')
```

#### => A.L. studio albums global sales decreased with time
#### => A.L. studio albums US chart debut worsened with time


```python
albums_selection = df_albums[["year", "label", "producers"]]

pd.set_option('max_colwidth', 120)

albums_selection
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>year</th>
      <th>label</th>
      <th>producers</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>2002</td>
      <td>[Arista Records]</td>
      <td>[L.A. Reid, The Matrix, Clif Magness, Curt Frasca, Peter Zizzo]</td>
    </tr>
    <tr>
      <td>1</td>
      <td>2004</td>
      <td>[Arista Records, RCA Records]</td>
      <td>[Raine Maida, Don Gilmore, Butch Walker]</td>
    </tr>
    <tr>
      <td>2</td>
      <td>2007</td>
      <td>[RCA Records]</td>
      <td>[Avril Lavigne, Deryck Whibley, Butch Walker, Rob Cavallo, Dr. Luke, The Submarines, Jesse Welch, Steven Wolf]</td>
    </tr>
    <tr>
      <td>3</td>
      <td>2011</td>
      <td>[RCA Records]</td>
      <td>[Avril Lavigne, Deryck Whibley, Butch Walker, Max Martin, Shellback]</td>
    </tr>
    <tr>
      <td>4</td>
      <td>2013</td>
      <td>[Epic Records]</td>
      <td>[Avril Lavigne, L.A. Reid, Martin Johnson, Peter Svensson, David Hodges, Matt Squire, Chad Kroeger]</td>
    </tr>
    <tr>
      <td>5</td>
      <td>2019</td>
      <td>[BMG]</td>
      <td>[Avril Lavigne, Stephan Moccio, Chris Baseford, Johan Carlsson, Lauren Christy, Ryan Cabrera, Chad Kroeger]</td>
    </tr>
  </tbody>
</table>
</div>



#### => Frequent change of producers, changed labels several time

## Avril Lavigne's backing band

[3]

<img src="img/al_band_timeline.png" title="Lavigne band timeline" />

* 2nd album (2004): 1 new musician (since the previous album)
* 3rd album (2007): 6 new musicians
* 4th album (2011): 1 new musician
* 5th album (2013): 2 new musicians
* 6th album (2019): 2 new musicians

#### => There is no one left from the original band, they stayed for the first or two first albums
#### The 3rd album has the most new band members.

## Avril Lavigne's songs

[6]


```python
al_songs = pd.read_csv('al_songs_spotify_data.csv')
```


```python
al_songs.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>title</th>
      <th>artist</th>
      <th>top genre</th>
      <th>year</th>
      <th>added</th>
      <th>Beats per minute</th>
      <th>energy</th>
      <th>danceability</th>
      <th>Loudness (dB)</th>
      <th>liveness</th>
      <th>valence</th>
      <th>duration</th>
      <th>acousticness</th>
      <th>speechiness</th>
      <th>popularity</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>Complicated</td>
      <td>Avril Lavigne</td>
      <td>canadian pop</td>
      <td>2002</td>
      <td>2020‑03‑05</td>
      <td>78</td>
      <td>78</td>
      <td>59</td>
      <td>-6</td>
      <td>30</td>
      <td>43</td>
      <td>245</td>
      <td>6</td>
      <td>5</td>
      <td>76</td>
    </tr>
    <tr>
      <td>1</td>
      <td>Sk8er Boi</td>
      <td>Avril Lavigne</td>
      <td>canadian pop</td>
      <td>2002</td>
      <td>2020‑03‑05</td>
      <td>150</td>
      <td>90</td>
      <td>49</td>
      <td>-4</td>
      <td>36</td>
      <td>48</td>
      <td>204</td>
      <td>0</td>
      <td>5</td>
      <td>74</td>
    </tr>
    <tr>
      <td>2</td>
      <td>What the Hell</td>
      <td>Avril Lavigne</td>
      <td>canadian pop</td>
      <td>2011</td>
      <td>2020‑03‑05</td>
      <td>150</td>
      <td>93</td>
      <td>58</td>
      <td>-4</td>
      <td>14</td>
      <td>88</td>
      <td>221</td>
      <td>0</td>
      <td>5</td>
      <td>73</td>
    </tr>
    <tr>
      <td>3</td>
      <td>Girlfriend</td>
      <td>Avril Lavigne</td>
      <td>canadian pop</td>
      <td>2007</td>
      <td>2020‑03‑05</td>
      <td>164</td>
      <td>96</td>
      <td>56</td>
      <td>-2</td>
      <td>21</td>
      <td>67</td>
      <td>217</td>
      <td>0</td>
      <td>10</td>
      <td>72</td>
    </tr>
    <tr>
      <td>4</td>
      <td>Head Above Water</td>
      <td>Avril Lavigne</td>
      <td>canadian pop</td>
      <td>2019</td>
      <td>2020‑03‑05</td>
      <td>130</td>
      <td>69</td>
      <td>58</td>
      <td>-5</td>
      <td>10</td>
      <td>27</td>
      <td>221</td>
      <td>1</td>
      <td>7</td>
      <td>71</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Add an 'album' column
albums_content = {
    "album1": {"name": "Let Go", 
               "songs": ["Losing Grip", "Complicated", "Sk8er Boi", "I'm with You", "Mobile", "Unwanted",
                         "Tomorrow", "Anything but Ordinary", "Things I'll Never Say", "My World",
                         "Nobody's Fool", "Too Much to Ask", "Naked"]},
    "album2": {"name": "Under My Skin", 
               "songs": ["Take Me Away", "Together", "Don't Tell Me", "He Wasn't",
                         "How Does It Feel", "My Happy Ending", "Nobody's Home", "Forgotten",
                         "Who Knows", "Fall to Pieces", "Freak Out", "Slipped Away"]},
    "album3": {"name": "The Best Damn Thing", 
               "songs": ["Girlfriend", "I Can Do Better", "Runaway", "The Best Damn Thing",
                         "When You're Gone", "Everything Back but You", "Hot", "Innocence",
                         "I Don't Have to Try", "One of Those Girls", "Contagious", "Keep Holding On"]},
    "album4": {"name": "Goodbye Lullaby", 
               "songs": ["Black Star", "What the Hell", "Push", "Wish You Were Here", "Smile",
                         "Stop Standing There", "I Love You", "Everybody Hurts", "Not Enough",
                         "4 Real", "Darlin", "Remember When", "Goodbye", "Alice"]},
    "album5": {"name": "Avril Lavigne", 
               "songs": ["Rock n Roll", "Here's to Never Growing Up", "17", "Bitchin' Summer",
                         "Let Me Go", "Give You What You Like", "Bad Girl", "Hello Kitty",
                         "You Ain't Seen Nothin' Yet", "Sippin' On Sunshine", "Hello Heartache",
                         "Falling Fast", "Hush Hush"]},
    "album6": {"name": "Head Above Water", 
               "songs": ["Head Above Water", "Birdie", "I Fell in Love with the Devil",
                         "Tell Me It's Over", "Mailbox", "Dumb Blonde", "It Was In Me",
                         "Souvenir", "Crush", "Goddess", "Bigger Wow", "Love Me Insane", "Warrior"]}
    }
```


```python
import string

def clean_song_title(song_title):
    song_title = song_title.lower()
    song_title = song_title.split(" - ")[0]
    song_title = song_title.split(" (")[0]
    return song_title
```


```python
for k, v in albums_content.items():
    v["songs"] = [clean_song_title(song) for song in v["songs"]]
```


```python
def get_album_names(title):
    title = clean_song_title(title)
    if title in albums_content["album1"]["songs"]:
        return albums_content["album1"]["name"]
    if title in albums_content["album2"]["songs"]:
        return albums_content["album2"]["name"]
    if title in albums_content["album3"]["songs"]:
        return albums_content["album3"]["name"]
    if title in albums_content["album4"]["songs"]:
        return albums_content["album4"]["name"]
    if title in albums_content["album5"]["songs"]:
        return albums_content["album5"]["name"]
    if title in albums_content["album6"]["songs"]:
        return albums_content["album6"]["name"]
```


```python
# Add empty 'album' album
al_songs.assign(album="")
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>title</th>
      <th>artist</th>
      <th>top genre</th>
      <th>year</th>
      <th>added</th>
      <th>Beats per minute</th>
      <th>energy</th>
      <th>danceability</th>
      <th>Loudness (dB)</th>
      <th>liveness</th>
      <th>valence</th>
      <th>duration</th>
      <th>acousticness</th>
      <th>speechiness</th>
      <th>popularity</th>
      <th>album</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>Complicated</td>
      <td>Avril Lavigne</td>
      <td>canadian pop</td>
      <td>2002</td>
      <td>2020‑03‑05</td>
      <td>78</td>
      <td>78</td>
      <td>59</td>
      <td>-6</td>
      <td>30</td>
      <td>43</td>
      <td>245</td>
      <td>6</td>
      <td>5</td>
      <td>76</td>
      <td></td>
    </tr>
    <tr>
      <td>1</td>
      <td>Sk8er Boi</td>
      <td>Avril Lavigne</td>
      <td>canadian pop</td>
      <td>2002</td>
      <td>2020‑03‑05</td>
      <td>150</td>
      <td>90</td>
      <td>49</td>
      <td>-4</td>
      <td>36</td>
      <td>48</td>
      <td>204</td>
      <td>0</td>
      <td>5</td>
      <td>74</td>
      <td></td>
    </tr>
    <tr>
      <td>2</td>
      <td>What the Hell</td>
      <td>Avril Lavigne</td>
      <td>canadian pop</td>
      <td>2011</td>
      <td>2020‑03‑05</td>
      <td>150</td>
      <td>93</td>
      <td>58</td>
      <td>-4</td>
      <td>14</td>
      <td>88</td>
      <td>221</td>
      <td>0</td>
      <td>5</td>
      <td>73</td>
      <td></td>
    </tr>
    <tr>
      <td>3</td>
      <td>Girlfriend</td>
      <td>Avril Lavigne</td>
      <td>canadian pop</td>
      <td>2007</td>
      <td>2020‑03‑05</td>
      <td>164</td>
      <td>96</td>
      <td>56</td>
      <td>-2</td>
      <td>21</td>
      <td>67</td>
      <td>217</td>
      <td>0</td>
      <td>10</td>
      <td>72</td>
      <td></td>
    </tr>
    <tr>
      <td>4</td>
      <td>Head Above Water</td>
      <td>Avril Lavigne</td>
      <td>canadian pop</td>
      <td>2019</td>
      <td>2020‑03‑05</td>
      <td>130</td>
      <td>69</td>
      <td>58</td>
      <td>-5</td>
      <td>10</td>
      <td>27</td>
      <td>221</td>
      <td>1</td>
      <td>7</td>
      <td>71</td>
      <td></td>
    </tr>
    <tr>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <td>70</td>
      <td>Black Star</td>
      <td>Avril Lavigne</td>
      <td>canadian pop</td>
      <td>2011</td>
      <td>2020‑03‑05</td>
      <td>128</td>
      <td>33</td>
      <td>54</td>
      <td>-9</td>
      <td>19</td>
      <td>20</td>
      <td>94</td>
      <td>61</td>
      <td>3</td>
      <td>41</td>
      <td></td>
    </tr>
    <tr>
      <td>71</td>
      <td>4 Real</td>
      <td>Avril Lavigne</td>
      <td>canadian pop</td>
      <td>2011</td>
      <td>2020‑03‑05</td>
      <td>78</td>
      <td>84</td>
      <td>52</td>
      <td>-6</td>
      <td>11</td>
      <td>28</td>
      <td>208</td>
      <td>0</td>
      <td>3</td>
      <td>41</td>
      <td></td>
    </tr>
    <tr>
      <td>72</td>
      <td>Sippin' On Sunshine</td>
      <td>Avril Lavigne</td>
      <td>canadian pop</td>
      <td>2013</td>
      <td>2020‑03‑05</td>
      <td>176</td>
      <td>73</td>
      <td>55</td>
      <td>-7</td>
      <td>32</td>
      <td>56</td>
      <td>209</td>
      <td>0</td>
      <td>12</td>
      <td>41</td>
      <td></td>
    </tr>
    <tr>
      <td>73</td>
      <td>Goodbye</td>
      <td>Avril Lavigne</td>
      <td>canadian pop</td>
      <td>2011</td>
      <td>2020‑03‑05</td>
      <td>167</td>
      <td>33</td>
      <td>18</td>
      <td>-7</td>
      <td>13</td>
      <td>24</td>
      <td>272</td>
      <td>72</td>
      <td>3</td>
      <td>40</td>
      <td></td>
    </tr>
    <tr>
      <td>74</td>
      <td>You Ain't Seen Nothin' Yet</td>
      <td>Avril Lavigne</td>
      <td>canadian pop</td>
      <td>2013</td>
      <td>2020‑03‑05</td>
      <td>145</td>
      <td>90</td>
      <td>56</td>
      <td>-4</td>
      <td>7</td>
      <td>67</td>
      <td>193</td>
      <td>0</td>
      <td>6</td>
      <td>40</td>
      <td></td>
    </tr>
  </tbody>
</table>
<p>75 rows × 16 columns</p>
</div>




```python
for idx, row in al_songs.iterrows():
    album_name = get_album_names(row.title)
    al_songs.loc[idx, "album"] = album_name
```


```python
al_songs.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>title</th>
      <th>artist</th>
      <th>top genre</th>
      <th>year</th>
      <th>added</th>
      <th>Beats per minute</th>
      <th>energy</th>
      <th>danceability</th>
      <th>Loudness (dB)</th>
      <th>liveness</th>
      <th>valence</th>
      <th>duration</th>
      <th>acousticness</th>
      <th>speechiness</th>
      <th>popularity</th>
      <th>album</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>Complicated</td>
      <td>Avril Lavigne</td>
      <td>canadian pop</td>
      <td>2002</td>
      <td>2020‑03‑05</td>
      <td>78</td>
      <td>78</td>
      <td>59</td>
      <td>-6</td>
      <td>30</td>
      <td>43</td>
      <td>245</td>
      <td>6</td>
      <td>5</td>
      <td>76</td>
      <td>Let Go</td>
    </tr>
    <tr>
      <td>1</td>
      <td>Sk8er Boi</td>
      <td>Avril Lavigne</td>
      <td>canadian pop</td>
      <td>2002</td>
      <td>2020‑03‑05</td>
      <td>150</td>
      <td>90</td>
      <td>49</td>
      <td>-4</td>
      <td>36</td>
      <td>48</td>
      <td>204</td>
      <td>0</td>
      <td>5</td>
      <td>74</td>
      <td>Let Go</td>
    </tr>
    <tr>
      <td>2</td>
      <td>What the Hell</td>
      <td>Avril Lavigne</td>
      <td>canadian pop</td>
      <td>2011</td>
      <td>2020‑03‑05</td>
      <td>150</td>
      <td>93</td>
      <td>58</td>
      <td>-4</td>
      <td>14</td>
      <td>88</td>
      <td>221</td>
      <td>0</td>
      <td>5</td>
      <td>73</td>
      <td>Goodbye Lullaby</td>
    </tr>
    <tr>
      <td>3</td>
      <td>Girlfriend</td>
      <td>Avril Lavigne</td>
      <td>canadian pop</td>
      <td>2007</td>
      <td>2020‑03‑05</td>
      <td>164</td>
      <td>96</td>
      <td>56</td>
      <td>-2</td>
      <td>21</td>
      <td>67</td>
      <td>217</td>
      <td>0</td>
      <td>10</td>
      <td>72</td>
      <td>The Best Damn Thing</td>
    </tr>
    <tr>
      <td>4</td>
      <td>Head Above Water</td>
      <td>Avril Lavigne</td>
      <td>canadian pop</td>
      <td>2019</td>
      <td>2020‑03‑05</td>
      <td>130</td>
      <td>69</td>
      <td>58</td>
      <td>-5</td>
      <td>10</td>
      <td>27</td>
      <td>221</td>
      <td>1</td>
      <td>7</td>
      <td>71</td>
      <td>Head Above Water</td>
    </tr>
  </tbody>
</table>
</div>




```python
# al_songs.to_csv('al_songs_spotify_data_with_albums.csv', index=False)
```

<img src="img/oym_properties.png" title="Properties in the Organize Your Music analysis" />


```python
# Tempo (BPM)
chart3 = alt.Chart(al_songs, width=200, height=200).mark_boxplot(opacity=0.7).encode(
    x='year:O',
    y='Beats per minute:Q',
    color=alt.Color('album', sort=['year']),
    tooltip=['title', 'Beats per minute']
).interactive()

# Energy
chart4 = alt.Chart(al_songs, width=200, height=200).mark_boxplot(opacity=0.7).encode(
    x='year:O',
    y='energy:Q',
    color=alt.Color('album', sort=['year']),
    tooltip=['title', 'energy']
).interactive()

# Danceability
chart5 = alt.Chart(al_songs, width=200, height=200).mark_boxplot(opacity=0.7).encode(
    x='year:O',
    y='danceability:Q',
    color=alt.Color('album', sort=['year']),
    tooltip=['title', 'danceability']
).interactive()

# Positive Mood (Valence)
chart6 = alt.Chart(al_songs, width=300, height=300).mark_boxplot(opacity=0.7).encode(
    x='year:O',
    y='valence:Q',
    color=alt.Color('album', sort=['year']),
    tooltip=['title', 'valence']
).interactive()

# Acousticness
chart7 = alt.Chart(al_songs, width=300, height=300).mark_boxplot(opacity=0.7).encode(
    x='year:O',
    y='acousticness:Q',
    color=alt.Color('album', sort=['year']),
    tooltip=['title', 'acousticness']
).interactive()

# Speechiness
chart8 = alt.Chart(al_songs, width=300, height=300).mark_boxplot(opacity=0.7).encode(
    x='year:O',
    y='speechiness:Q',
    color=alt.Color('album', sort=['year']),
    tooltip=['title', 'speechiness']
).interactive()

# Popularity
chart9 = alt.Chart(al_songs, width=300, height=300).mark_boxplot(opacity=0.7).encode(
    x='year:O',
    y='popularity:Q',
    color=alt.Color('album', sort=['year']),
    tooltip=['title', 'popularity']
).interactive()
```


```python
# Tempo (BPM) | Energy | Danceability
chart3 | chart4 | chart5
```


    <vega.vegalite.VegaLite at 0x7f08a5f9a048>





    




![png](output_32_2.png)



```python
# alt.hconcat(chart3, chart4, chart5).save('plots/charts345.json')
# alt.hconcat(chart3, chart4, chart5).save('plots/charts345.html')
```


```python
# Positive Mood (Valence) | # Acousticness
chart6 | chart7
```


    <vega.vegalite.VegaLite at 0x7f08dc9a6630>





    




![png](output_34_2.png)



```python
# alt.hconcat(chart6, chart7).save('plots/charts67.json')
# alt.hconcat(chart6, chart7).save('plots/charts67.html')
```


```python
# Speechiness | Popularity
chart8 | chart9
```


    <vega.vegalite.VegaLite at 0x7f08dc122668>





    




![png](output_36_2.png)



```python
# alt.hconcat(chart8, chart9).save('plots/charts89.json')
# alt.hconcat(chart8, chart9).save('plots/charts89.html')
```


```python
# Energy vs acousticness
chart10 = alt.Chart(al_songs, width=200, height=200).mark_point(size=100, filled=True, opacity=0.7).encode(
    x='energy:Q',
    y='acousticness:Q',
    color=alt.Color('album', sort=['year']),
    tooltip=['title', 'album']
).interactive()

# Energy vs speechiness
chart11 = alt.Chart(al_songs, width=200, height=200).mark_point(size=100, filled=True, opacity=0.7).encode(
    x='energy:Q',
    y='speechiness:Q',
    color=alt.Color('album', sort=['year']),
    tooltip=['title', 'album']
).interactive()

# Acousticness vs speechiness
chart12 = alt.Chart(al_songs, width=200, height=200).mark_point(size=100, filled=True, opacity=0.7).encode(
    x='acousticness:Q',
    y='speechiness:Q',
    color=alt.Color('album', sort=['year']),
    tooltip=['title', 'album']
).interactive()
```


```python
# Energy vs acousticness | Energy vs speechiness |Acousticness vs speechiness
chart10 | chart11 | chart12
```


    <vega.vegalite.VegaLite at 0x7f08a5de4b00>





    




![png](output_39_2.png)



```python
# alt.hconcat(chart10, chart11, chart12).save('plots/charts101113.json')
# alt.hconcat(chart10, chart11, chart12).save('plots/charts101112.html')
```

#### => Musically, there are a lot of similarities overall.

#### Using songs from an open Spotify playlist [6] shows differences in energy and acousticness. The energy of her albums increased until the third album and then decreased. The songs are also more and more acoustic as time goes by. In terms of lyrics, the third, fifth and sixth albums seem to have more word content that the first, second and fourth albums.

- Albums 1, 2, 3: more energy
- Albums 4, 5, 6: more acoustic
- Albums 3, 5, 6: more words

## A bit of industry context


```python
women_singers_2000s = pd.read_csv('popular_women_artists_2000s.csv')
```


```python
women_singers_2000s.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>artist</th>
      <th>year</th>
      <th>global album sales</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>Adele</td>
      <td>2008</td>
      <td>8560000</td>
    </tr>
    <tr>
      <td>1</td>
      <td>Adele</td>
      <td>2011</td>
      <td>30140000</td>
    </tr>
    <tr>
      <td>2</td>
      <td>Adele</td>
      <td>2015</td>
      <td>20410000</td>
    </tr>
    <tr>
      <td>3</td>
      <td>Alicia Keys</td>
      <td>2001</td>
      <td>12600000</td>
    </tr>
    <tr>
      <td>4</td>
      <td>Alicia Keys</td>
      <td>2003</td>
      <td>8000000</td>
    </tr>
  </tbody>
</table>
</div>



This is subjective, I'm selecting a few women solo singers (amongst popular women artists in the 2000's) that I want to compare to Avril Lavigne.


```python
# Trying to select for more comparable artists
artists_selection = ["Avril Lavigne", "Britney Spears", "Christina Aguilera", 
                     "Katy Perry", "Pink", "Taylor Swift"]
```


```python
women_singers_selection = women_singers_2000s.loc[women_singers_2000s.artist.isin(artists_selection)];
```


```python
chart13 = alt.Chart(women_singers_selection, width=600, height=400).mark_line(size=5, opacity=0.8).encode(
    x='year:O',
    y='global album sales:Q',
    color=alt.Color('artist')
)

chart13
```


    <vega.vegalite.VegaLite at 0x7f310890a2e8>





    




![png](output_48_2.png)



```python
chart13.save('plots/chart13.json')
```

It seems Avril Lavigne started her career with high record sales when looking at other solo women artists of the early 2000's like Britney Spears and Christina Aguilera. Those two artists have been very feminine (and sexualised) from the beginning of their singing career and their sales pattern also when down. It therefore doesn't seem like a more feminine appearance would have been a strategy for reaching out to the public.
This could be different past 2014 when creating a following on social media platform (like Instagram) would rely even more on the artists appearance.

**References**

Conspiracy
* [1] https://www.theguardian.com/lifeandstyle/shortcuts/2017/may/15/avril-lavigne-melissa-cloning-conspiracy-theories
* [2] https://avrilestamorta.blogspot.com/

Data for analysis
* [3] https://en.wikipedia.org/wiki/Avril_Lavigne
* [4] https://en.wikipedia.org/wiki/Avril_Lavigne_discography
* [5] https://chartmasters.org/2018/02/cspc-avril-lavigne-popularity-analysis/9/
* [6] open Spotify playlist with all songs from studio recorded albums: https://open.spotify.com/playlist/1cVKLVWEFN2Be7tTA13qUj analyzed using http://organizeyourmusic.playlistmachinery.com (Powered by Spotify. Created by @plamere at The Science of Mu)
* [7] Global sales for each studio album of popular solo women artists between 2000 and 2015. Data from https://chartmasters.org/ - Note: I chose the album with higher sales when two albums are realised the same year (Shakira in 2005 and Jennifer Lopez in 2007) and looked only at English albums for Céline Dion.

Other
* [8] photos: https://avrillavigne.com/music/
* MTV docu, 2007: https://www.youtube.com/watch?v=f8GLe10jLSw


```python

```
