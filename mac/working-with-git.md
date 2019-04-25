---
title: Trabajo con Git
description: Empleo de Git en Visual Studio para Mac.
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 852B6A9D-AEFA-4EF4-A5DD-94A506019D20
ms.custom: video
ms.openlocfilehash: ba98312617aaf636ee388ec97f47c14ede75507d
ms.sourcegitcommit: 01334abf36d7e0774329050d34b3a819979c95a2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2019
ms.locfileid: "55852980"
---
# <a name="working-with-git"></a>Trabajo con Git

Git es un sistema de control de versiones distribuido que permite a los equipos trabajar en los mismos documentos de forma simultánea. Esto significa que hay un servidor central que contiene todos los archivos, pero que cada vez que se extrae un repositorio de este origen central, la totalidad del repositorio se clona en el equipo local.

En las siguientes secciones se analiza cómo usar Git para el control de versiones en Visual Studio para Mac.

## <a name="git-version-control-menu"></a>Menú Control de versiones de Git

En la imagen siguiente se ven las opciones proporcionadas en el elemento de menú Control de versiones de Visual Studio para Mac:

![Elemento de menú Control de versiones](media/version-control-gitVersionControlMenu.png)

## <a name="push-and-pull"></a>Envío e incorporación de cambios

El envío y la incorporación de cambios son dos de las acciones usadas con más frecuencia en Git. Para sincronizar cambios realizados por otros usuarios en el repositorio remoto, debe **incorporar los cambios** desde allí. Esto se hace en Visual Studio para Mac al seleccionar **Control de versiones > Actualizar solución**.

Una vez actualizados, revisados y confirmados los archivos, debe **enviarlos** al repositorio remoto para permitir a otros usuarios acceder a los cambios. Esto se hace en Visual Studio para Mac al seleccionar **Control de versiones > Insertar cambios**. Con esto se abre el cuadro de diálogo Insertar, que permite ver los cambios confirmados, y se selecciona la rama en la que insertar:

![Cuadro de diálogo que muestra la rama en la que confirmar](media/version-control-gitPush.png)

También puede confirmar y enviar los cambios al mismo tiempo, mediante el cuadro de diálogo Confirmar:

![Opción que muestra cómo confirmar y enviar al mismo tiempo.](media/version-control-commitPush.png)

## <a name="blame-log-and-merge"></a>Culpar, Registro y Combinar

En la parte inferior de la ventana hay cinco pestañas, como se muestra a continuación:

![Pestañas de Control de versiones](media/version-control-gitTabs.png)

Estas permiten las acciones siguientes:

* **Origen**: muestra el archivo de código fuente.
* **Cambios**: muestra el cambio en el código entre el archivo local y el archivo base. También puede comparar diferentes versiones del archivo a partir de hash distintos:

    ![Pestaña Cambios](media/version-control-gitChange.png)

* **Culpar**: muestra el nombre de usuario del usuario asociado a cada sección de código.
* **Registro**: muestra todas las confirmaciones, las horas, las fechas, los mensajes y los usuarios que son responsables del archivo:

    ![Pestaña Registro](media/version-control-gitLog.png)

* **Combinar**: se puede usar si existe un conflicto de combinación al confirmar el trabajo. Muestra una representación visual de los cambios realizados por el usuario y el otro desarrollador, lo que permite combinar ambas secciones de código sin problemas.

## <a name="switching-branches"></a>Cambio de ramas

De forma predeterminada, la primera rama creada en un repositorio se conoce como rama  **maestra** . Técnicamente no hay diferencias entre la rama maestra y las demás, aunque la maestra es la que en los equipos de desarrollo se suele considerar como la rama "activa" o de "producción".

Se puede crear una línea independiente de desarrollo al ramificar la rama maestra (o cualquier otra rama, de hecho). Esto proporciona una nueva versión de la rama maestra en un momento dado, lo que permite el desarrollo independientemente de lo que está "activo". El empleo de ramas de este modo se suele usar para características de desarrollo de software

Los usuarios pueden crear tantas ramas como quieran de cada repositorio, pero se recomienda que una vez que hayan terminado de usar una, se elimine para mantener el repositorio organizado.

Puede ver las ramas en Visual Studio para Mac si va a **Control de versiones > Administrar ramas y orígenes remotos...**:

![Vista Ramas](media/version-control-gitBranch2.png)

Para cambiar a otra rama, selecciónela en la lista y presione el botón **Cambiar a rama**.

Para crear una nueva rama, seleccione el botón **Nuevo** en el cuadro de diálogo de configuración del repositorio de Git. Escriba el nuevo nombre de rama:

![Creación de nueva rama](media/version-control-gitBranch.png)

También puede establecer una rama remota a la rama de _seguimiento_. Vea más información sobre ramas de seguimiento en la [documentación de Git](https://git-scm.com/book/en/v2/Git-Branching-Remote-Branches#Tracking-Branches).

Vea la rama actual en el Panel de solución, junto al nombre del proyecto:

 ![Rama actual mostrada en el Panel de solución](media/version-control-gitBranchName.png)

## <a name="reviewing-and-committing"></a>Revisión y confirmación

Para revisar los cambios en los archivos, use las pestañas Cambios, Culpar, Registro y Combinar de cada documento, tratadas anteriormente en este tema.

Revise todos los cambios en el proyecto al ir al elemento de menú **Control de versiones > Revisar solución y confirmar**:

![Vista de revisión de código](media/version-control-gitReviewCommit.png)

Esto permite ver todos los cambios de cada archivo de un proyecto con la opción Revertir, Crear una revisión o Confirmar.

Para confirmar un archivo en el repositorio remoto, presione **Confirmar**, escriba un mensaje de confirmación y confirme con el botón Confirmar:

![Confirmación de un archivo](media/version-control-gitCommit.png)

Una vez que haya confirmado los cambios, envíelos al repositorio remoto para que otros usuarios puedan verlos.

## <a name="related-video"></a>Vídeo relacionado

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Manage-Projects-with-Git/player]

## <a name="see-also"></a>Vea también

* [Share your code with Visual Studio 2017 and Azure Repos Git](/azure/devops/repos/git/share-your-code-in-git-vs-2017) (Compartir el código con Visual Studio 2017 y el repositorio Git de Azure Repos)