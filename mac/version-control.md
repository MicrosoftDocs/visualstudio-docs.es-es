---
title: Control de versiones
description: Empleo de Git y Subversion en Visual Studio para Mac.
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.assetid: 49917483-28AA-4598-A847-71F1F2E0DCB5
ms.openlocfilehash: c26cb512f0beb0dcfd47801d7a619ec78eb3cd32
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2018
---
# <a name="version-control"></a>Control de versiones

El control de versiones es un sistema para administrar archivos a lo largo de muchas versiones diferentes y, en el ámbito del desarrollo de software, lo usan muchos desarrolladores. El propósito principal de cualquier sistema de control de versiones (_VCS_) es encontrar una solución que permita a todos los usuarios trabajar en el código base al mismo tiempo.

En el núcleo de cualquier sistema de control de versiones hay un _repositorio_, que actúa como almacén central de datos para todos los distintos archivos, de forma similar a un servidor de archivos. Pero a diferencia de un servidor de archivos, el repositorio contiene todo el historial del proyecto y todas las revisiones que se han realizado.

Si el repositorio es el almacén de datos central, es lógico que cada usuario tenga un almacén local de los datos que le permita trabajar con ellos. Se denomina una _copia de trabajo_. En Visual Studio para Mac, la copia de trabajo aparecerá de la misma forma que cualquier otro directorio local en el equipo, lo que permite leer y escribir en cualquiera de los archivos. Pero dado que Visual Studio para Mac tiene integración del sistema de control de versiones, puede utilizar la eficacia de Subversion y Git sin salir del IDE.

Subversion es un sistema centralizado de control de versiones, lo que significa que hay un único servidor que contiene todos los archivos y las revisiones desde el que los usuarios pueden extraer del repositorio cualquier versión de cualquier archivo. Cuando se extraen archivos de un repositorio remoto de Subversion, el usuario obtiene una instantánea del repositorio en ese momento dado.

Git es un sistema de control de versiones distribuido que permite a los equipos trabajar en los mismos documentos de forma simultánea. Con Git puede haber un único servidor que contiene todos los archivos, pero que cada vez que se extrae un repositorio de este origen central, la totalidad del repositorio se clona localmente en su equipo.

## <a name="basic-concepts"></a>Conceptos básicos 

Visual Studio para Mac proporciona compatibilidad con los sistemas de control de versiones Git y Subversion. En los artículos siguientes se examina la configuración de los repositorios Git y Subversion mediante Visual Studio para Mac, así como funciones sencillas como revisar, confirmar y enviar cambios.

* [Configurar un repositorio GIT](~/set-up-git-repository.md) 
* [Trabajar con GIT](~/working-with-git.md)
* [Configurar un repositorio de Subversion](~/set-up-subversion-repository.md)
* [Trabajar con Subversion](~/working-with-subversion.md)