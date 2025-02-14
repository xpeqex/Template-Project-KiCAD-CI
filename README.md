# Plantilla para proyectos de ingeniería
Esta plantilla es la base para cualquier proyecto desarrollado en Electronic Cats.
Automaticamente, se generarán todos los archivos necesarios para la compra de material, fabricación y ensamble.
Así como documentos complementarios para un proyecto completo.

> Este README.md puede ser utilizado como plantilla para documentación, de esta manera se puede incluir generalidades, recomendaciones y todo lo necesario para entender el proyecto.

## ¿Como utilizar esta plantilla?
Para comenzar un nuevo proyecto, presiona el botón de "Use this template".

### KiCad
Para esta plantilla, el hardware debe de ser diseñado y/o desarrollado en KiCad 6.
Al termino del diseño del proyecto, KiCad deberá de generar los siguientes archivos:

- nombre_del_proyecto.kicad_pro
- nombre_de_la_pcb.kicad_pcb
- nombre_del_esquematico.kicad_sch

Además de archivos temporales, los cuales Git ignora al momento de cualquier push.
[Archivos ignorados](.gitignore)

Estos archivos deberán ser guardados dentro de la carpeta de [hardware](hardware/).

### Configuracion de automatizacion
Una vez terminado el proyecto, antes de hacer el primer Release, se deberán realizar algunos cambios para la automatizacion de archivos.
En la carpeta [.github/workflows](.github/workflows/) se encuentra el archivo kicad_kibot.yml, en donde los siguientes campos deberán ser modificados

```yaml
# optional - schematic file
schema: 'hardware/Template-KiCAD-Project-CI.kicad_sch'
# optional - pcb file
board: 'hardware/Template-KiCAD-Project-CI.kicad_pcb'
```
Se deberá reemplazar el nombre del archivo "Template-KiCAD-Project-CI" por el nombre del proyecto diseñado.
Es importante conservar las extensiones de archivo .kicad_sch y .kicad_pcb.

### Activar/desactivar DRC y ERC
Las opciones de DRC y ERC estarán siempre activas predeterminadamente, para desactivarlas se deberá de eliminar las siguientes lineas del archivo [electroniccats_sch.kibot.yaml](hardware/electroniccats_sch.kibot.yaml).
```yaml
  run_erc: true
  run_drc: true
```
Esta action solo correrá cada vez que se haga un release.

Si, además, se busca desactivar el DRC y el ERC cuando se haga push o pull request, es necesario eliminar el archivo [action_drc.yml](.github/workflows/action_drc.yml).

## Creacion de Release
Al terminar el proyecto y su revisión, se publicará el primer Release.
Para crear un nuevo Release, presiona el botón de "Create a new release".
Una vez creado el Release, podrás ver la creacion de los archivos en la sección de Actions.
Al terminar, los archivos serán generados en el mismo release.

## Maintainer

<a href="https://github.com/sponsors/ElectronicCats">
  <img src="https://electroniccats.com/wp-content/uploads/2020/07/Badge_GHS.png" height="104" />
</a>

Electronic Cats invests time and resources providing this open source design, please support Electronic Cats and open-source hardware by purchasing products from Electronic Cats!
