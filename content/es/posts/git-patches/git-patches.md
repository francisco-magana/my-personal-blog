---
title: "Git patches"
summary: "Sobre como usar git patch para almacenar cambios."
categories: ["git"]
tags: ["technical"]
#externalUrl: ""
#showSummary: true
date: 2024-11-02
draft: false
---

## ¿Que son los git patches?

Los patches son archivos que contienen código y metadata que Git puede entender y pueden ser aplicados nuevamente. Estos archivos pueden ser generados con los cambios actuales en diff o con los de algún commit en especifico.

Te pueden ser utiles en las siguientes situaciones:

- Le haz explicado a alguién como realizar algo y quieres que el pueda tener ese código en su entorno de desarrollo sin que tenga que escribirlo el también.
- Tienes un cambio que otro desarrollador necesita para continuar con su tarea asignada pero aún necesitas terminar y probar algunas cosas antes de abrir un pull request, pero estás seguro que ese código le puede servir para continuar.
- Un desarrollador ha sido asignado a una tarea en un proyecto en el que trabajaste y deseas compartirle algún hack que usaste para agilizar tu desarrollo.
- Has escrito un código que quieres almacenar para el futuro pero no quieres que se pierda en la larga lista de stash que tienes.

## Crear un patch

Crear un patch es muy sencillo, suelo usarlos de las siguientes formas:

### De cambios en tu directorio de trabajo

Si haz escrito el código en tu directorio de trabajo, puedes crear un patch usando el resultado del comando `git diff`:

`git diff > some_changes_i_want_to_share.patch`

Si solo quieres compartir los cambios de uno o más archivos en específico de tu directorio de trabajo puedes indicarlo de la siguiente manera:

`git diff file1.js > some_changes.patch`

`git diff file1.js file2.js > some_changes.patch`

### De un commit

Para poder almacenar los cambios de un commit en un patch puedes indicarlo de la siguiente manera:

`git format-patch [commit_hash]`

## El archivo .patch

Puedes abrir el archivo `.patch` en tu editor de código o IDE como cualquier archivo, deberás de ver el código incluido asi como la metadata adicional que git usará para aplicar el patch. Puedes verificar si estás almacenando correctamente lo que necesitas guardar o compartir.

## Aplicar un patch al directorio de trabajo

Para aplicar el patch es necesario usar el comando:

`git apply my_patch_file.patch`

Cuando uses `git apply` verás los cambios reflejados en tu directorio de trabajo. Aplicar un patch no generará un nuevo commit.

## Conclusión

El concepto de patches es muy sencillo de entender y resultan muy útiles al momento de trabajar con otros desarrolladores o para guardar código para el futuro. Trata de sacarles provecho para tu flujo de trabajo o el de tu equipo.