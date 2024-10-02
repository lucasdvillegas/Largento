# Proyecto: Argento League Database.

Los cambios realizados se van a ver reflejados en: https://argentoleague.com

## Autor

- [@lucasdvillegas](https://www.github.com/lucasdvillegas)

# Estructura de la pseudo base de datos.

La estructura de esta pseudo base de datos está compuesta por un objeto en general que es la liga en sí. Está va a contener los siguientes atributos:

```bash
{
  "edition": "Primera edición", #Tipo string o cadena, debe contener siempre comillas.
  "visible": true, #Tipo booleano, no debe contener comillas. Puede ser true o false.
  "teams": [], #Tipo arreglo
  "tables": [], #Tipo arreglo
  "journeys": [], #Tipo arreglo
}
```

#### AVISO: Todos los atributos mencionados deberán ser respetados tanto por su tipo de dato como lenguaje. Es decir, NO pueden ser traducidos al español.

Para crear una nueva liga esta deberá respetar el formato mostrado anteriormente, esta debe contener como nombre el número que le precede. Es decir, la próxima edición deberá crearse como "2.json".

# Atributo "edition".

El atributo "edition" marca la edición de la liga, este se verá reflejado en un botón de tipo dropdown por lo cual se debe respetar el tipo de dato y formato. Es decir, la próximas ligas deberán llamarse "Segunda edición", "Tercera..", etc.

```bash
{
  "edition": "Primera edición",
}
```

# Atributo "visible".

El atributo "visible" activará el acceso a la siguiente liga o la actual. Este puede adoptar 2 valores true o false.

```bash
{
  "visible": true,
}
```

# Atributo "teams".

El atributo "teams" es un arreglo de objetos [{}, {}, {}], es decir, puede contener muchos equipos, con sus propios atributos.

```bash
{
  "teams": [],
}
```

## Atributo "teams" - Cargar/Editar Equipo.

Cada equipo va a contener los siguientes atributos:

```bash
{
  "team_name": "The Rats", #Nombre del equipo
  "team_logo": "", #URL del logo del equipo
  "team_players": [] #Arreglo de participantes
}
```

Ejemplo de como debería ser cargado un equipo:

```bash
{
  "team_name": "The Rats",
  "team_logo": "https://raw.githubusercontent.com/lucasdvillegas/liga_teams_json/refs/heads/main/teams_icons/the_rats_logo.png",
  "team_players": [
  {
    "name": "Vitaly!",
    "range": "https://raw.githubusercontent.com/lucasdvillegas/liga_teams_json/refs/heads/main/medals/legend_medal.png"
  },
  {
    "name": "Beto",
    "range": "https://raw.githubusercontent.com/lucasdvillegas/liga_teams_json/refs/heads/main/medals/divine_medal.png"
  },
  {
    "name": "SSJGSSJ",
    "range": "https://raw.githubusercontent.com/lucasdvillegas/liga_teams_json/refs/heads/main/medals/divine_medal.png"
  }
}
```

Podemos ver que el atributo "team_players" es un arreglo "[]" que está compuesto por objetos "{}" con sus propios atributos, en este caso "name" y "range". Ambos atributos son de tipo string o cadena, es decir texto alfanumérico, este debe estar siempre en comillas. Un jugador se compone de su nombre y una URL que apunta al icon de su medalla.

```bash
{
  "name": "Priss BOT", #Nombre del jugador
  "range": "https://raw.githubusercontent.com/lucasdvillegas/liga_teams_json/refs/heads/main/medals/arcont_medal.png" #Dirección URL a imagen de su medalla
}
```

# Atributo "tables".

El atributo "tables" quizás es un poquito complejo ya que se compone de un arreglo de arreglos de objetos [[{}, {}, {}], [{}, {}, {}], [{}, {}, {}]].
Cada arreglo dentro del arreglo principal [[], []] representa una tabla, los objetos dentro de del arreglo hijo son los equipos participantes.

En esta ocasión cada equipo va a contener 
 ```bash
{
   "team": "Gatitos Techeros Gaming",
   "logo": "https://raw.githubusercontent.com/lucasdvillegas/liga_teams_json/refs/heads/main/teams_icons/gatitos_techeros_gaming.png",
   "games": 2,
   "w": 1,
   "l": null,
   "d": 1,
   "puntos": 3
 }
```

## Atributo "tables" - Cargar/Editar Tablas.

Ejemplo de como cargar 2 tablas compuestas por 2 equipos cada una. Se podría decir que la primera tabla es un grupo, y la segunda es otro. Para agregar una tercera tabla quedaría agregar un arreglo más al arreglo padre con sus respectivos equipos.

 ```bash
[
    [
      {
        "team": "Gatitos Techeros Gaming",
        "logo": "https://raw.githubusercontent.com/lucasdvillegas/liga_teams_json/refs/heads/main/teams_icons/gatitos_techeros_gaming.png",
        "games": 2,
        "w": 1,
        "l": null,
        "d": 1,
        "puntos": 3
      },
      {
        "team": "Hydra E-sport",
        "logo": "https://raw.githubusercontent.com/lucasdvillegas/liga_teams_json/refs/heads/main/teams_icons/hydra_esport.png",
        "games": 2,
        "w": null,
        "l": 1,
        "d": 1,
        "puntos": 1
      }
    ],
    [
      {
        "team": "Epicenter",
        "logo": "https://raw.githubusercontent.com/lucasdvillegas/liga_teams_json/refs/heads/main/teams_icons/epicenter.png",
        "games": 2,
        "w": 1,
        "l": null,
        "d": 1,
        "puntos": 3
      },
      {
        "team": "Los Atiende Boludos",
        "logo": "https://raw.githubusercontent.com/lucasdvillegas/liga_teams_json/refs/heads/main/teams_icons/los_atiende_boludos.png",
        "games": 2,
        "w": 1,
        "l": null,
        "d": 1,
        "puntos": 3
      }
    ]
 ]
```

# Atributo "journeys".

El atributo journeys quizás sea también un poco más complejo que el anterior, este es un arreglo de arreglos de arreglos de objetos. Es decir:

```bash
  "journeys": [ #Arreglo padre - representa el total de cantidad de jornadas
    [ #Arreglo hijo - representa la cantidad de fechas
      [ #Arreglo nieto - representa la cantidad de equipos que van a jugar dentro de esta fecha
        {
          "team": "Anxiety",
          "resultado": 2
        },
        {
          "team": "NoLegion",
          "resultado": 0
        }
      ]
    ],
    [
    ]
  ]
```

Ejemplo de cómo cargar el atributo journeys:

```bash
"journeys": [
    [
      [
        {
          "team": "Anxiety",
          "resultado": 2
        },
        {
          "team": "NoLegion",
          "resultado": 0
        }
      ],
      [
        {
          "team": "Branca Team",
          "resultado": 2
        },
        {
          "team": "Hydra E-Sport",
          "resultado": 0
        }
      ]
    ],
    [
      [
        {
          "team": "Gatitos Techeros Gaming",
          "resultado": 1
        },
        {
          "team": "Anxiety",
          "resultado": 1
        }
      ],
      [
        {
          "team": "NoLegion",
          "resultado": 1
        },
        {
          "team": "Hydra E-Sport",
          "resultado": 1
        }
      ]
    ]
  ]
```

En este ejemplo vemos como "journeys" está compuesta por 2 jornadas, primera jornada compuesta por 2 fechas y 4 equipos en total. La segunda jornada sigue el mismo formato hilo también.

#### AVISO: No existe límite de fechas o cantidad de jornadas pero se espera que cada fecha SOLO esté compuesta por 2 equipos, ya que las tablas están preparadas para cargar 2 equipos por fecha.
