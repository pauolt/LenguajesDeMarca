# **Grieta del Invocador**

## **DTD**

#### 1. `grieta_del_invocador`
- Elemento raíz que contiene `equipos` y `modo`.

```
<!ELEMENT grieta_del_invocador (equipos, modo)>
```

#### 2. `equipos`
- Contiene uno o más `equipo`.
```
<!ELEMENT equipos (equipo+)>
```

#### 3. `modo`
- Indica el modo de juego como texto (por ejemplo, "clasificatoria").
```
<!ELEMENT modo (#PCDATA)>
```
#### 4. `equipo`
- Representa un `equipo`, con los subelementos:
 - `jugador+`: Uno o más jugadores en el equipo.
 - `oro_total`: Oro total acumulado por el equipo.
 - `minions_totales`: Total de minions asesinados por el equipo.
 - `dragones`: Dragones capturados por el equipo.

- Atributo:
 - `equipo`: Identificador único del equipo (obligatorio).
```
<!ELEMENT equipo (jugador+, oro_total, minions_totales, dragones)> <!ATTLIST equipo equipo ID #REQUIRED>
```
#### 5. `color`
- Indica el color del equipo.
```
<!ELEMENT color (#PCDATA)>
```

#### 6. `oro_total`
- `oro_total`: Representa el oro acumulado por el equipo.
```
<!ELEMENT oro_total (#PCDATA)> 
```

#### 7. `minions_totales`
- `minions_totales`: Representa el total de minions asesinados por el equipo.
```
<!ELEMENT minions_totales (#PCDATA)>
```

#### 8. `dragones`
- Contiene uno o más casos de `dragon`.
```
<!ELEMENT dragones (dragon*)>
```

#### 9. `dragon`
- Representa un `dragón` con atributo `tipo` que indica el tipo de dragón capturado.

- Atributo:
 - `tipo`: Tipo de dragón capturado (opcional).
```
<!ELEMENT dragon EMPTY> <!ATTLIST dragon tipo (infernal | oceano | montaña | nube | anciano | hextech | chemtech) #IMPLIED>
```
#### 10. `jugador`
- Representa un `jugador` con subelementos:
 - `nombre`: Nombre del jugador.
 - `personaje`: Personaje que utiliza, con atributos y subelementos asociados.
 - `minions`: Minions asesinados por el jugador.
 - `oro`: Oro acumulado por el jugador.
 - `objetos`: Cantidad de objetos que posee.

- Atributo:
 - `equipo`: Referencia al identificador del equipo al que pertenece.
```
<!ELEMENT jugador (nombre, personaje, minions, oro, objetos)> <!ATTLIST jugador equipo IDREF #IMPLIED>
```

#### 11. `nombre`
- Nombre del `jugador` o `personaje`.
```
<!ELEMENT nombre (#PCDATA)>
```
#### 12. `personaje`
- Representa el `personaje` que utiliza el `jugador`, con atributos y subelementos:

- Atributos:
 - `nivel`: Nivel del personaje (obligatorio).
 - `clase`: Clase del personaje (obligatorio).

- Subelementos:
 - `nombre`: Nombre del personaje.
 - `imagen`: Imagen del personaje.
 - `habilidades`: Habilidades de personaje.
 - `hechizos`: Hechizos del personaje, contiene uno o más `hechizo`.
 - `mana`: Un personaje puede consumir mana o no con cada habilidad.
 - `energia`: Un personaje puede consumir energia o no con cada habilidad.
 - `AD`: Daño que realizan algunos personajes con ataques basicos o también habilidades.
 - `AP`: Daño que realizan algunos personajes con las habilidades
 - `DEF`: Defensa de los personajes.
 - `ATTSPD`: Velocidad de los ataques basicos.
 - `MOVSPD`: Velocidad de movimiento.
 - `OMNSC`: Robo de vida.
```
<!ELEMENT personaje (nombre, imagen, habilidades, hechizos, mana?, energia?, AD, AP, DEF, ATTSPD, MOVSPD, OMNSC)> <!ATTLIST personaje nivel CDATA #REQUIRED> <!ATTLIST personaje clase (tanque | mago | asesino | luchador | tirador | soporte) #REQUIRED>
```
#### 13. `imagen`
- URL de la `imagen` del `personaje`.
```
<!ELEMENT imagen EMPTY> <!ATTLIST imagen url CDATA #REQUIRED>
```

#### 14. `habilidades` y `habilidad`
- Habilidades contiene una o más habilidad, cada una con subelementos:
 - `coste`: Coste de la `habilidad`.
 - `tipo`: Tipo de `habilidad` (opcional).
 - `descripcion`: Descripción de la `habilidad`. 

- Atributo:
 - `tecla`: Tecla asignada a la `habilidad` (obligatorio).
```
<!ELEMENT habilidades (habilidad+)> <!ATTLIST habilidades recurso (mana | energia | vida | nada) #REQUIRED> <!ELEMENT habilidad (coste, tipo?, descripcion)> <!ATTLIST habilidad tecla (Q | W | E | R) #REQUIRED>
```
