---
title: Trabajar con Subversion | Microsoft Docs
description: Empleo de Subversion en Visual Studio para Mac.
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 2400ED9C-6236-4C0A-A3AB-9D7CBE1F0CF4
ms.openlocfilehash: 026e3625b4ee2d6582ce5539e5cab68c945f09c0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="working-with-subversion"></a>Trabajar con Subversion

Como se ha mencionado anteriormente en este artículo, Subversion es el sistema de control de versiones centralizado que permite extraer del repositorio una única copia maestra de los datos centralizados. A diferencia de Git, la extracción de un repositorio de Subversion no clona la totalidad del repositorio, sino que solo toma una instantánea en ese momento dado.

Subversion usa un modelo Copiar-Modificar-Combinar para permitir que los usuarios trabajen simultáneamente en el mismo repositorio. Esto significa que cada usuario crea una copia local, o de trabajo, de los datos centralizados en la que luego puede trabajar de forma independiente. Los cambios en las copias de trabajo de los usuarios se combinan de forma cronológica.

Por ejemplo, imagine que el usuario A y el usuario B extraen una copia del repositorio remoto y cada uno modifica archivos. El usuario A termina las modificaciones y las confirma de forma remota. Antes de que el usuario B confirme su trabajo, tiene que actualizar su copia de trabajo con los cambios del repositorio remoto, es decir, mediante la combinación de los cambios del usuario A.

En las siguientes secciones se analiza cómo usar Subversion para el control de versiones en Visual Studio para Mac.

En la imagen siguiente se ven las opciones proporcionadas en el elemento de menú Control de versiones de Visual Studio para Mac:

![Elemento de menú Control de versiones](media/version-control-svnVersionControlMenu.png)

En las secciones siguientes se explica cada opción más detalladamente.

## <a name="checkout"></a>Extraer del repositorio...

Antes de empezar a usar un repositorio remoto de Subversion, debe extraer el repositorio para crear una copia local, o de trabajo, de ese directorio en el equipo local.

Para obtener más información sobre el uso de la característica **Extraer del repositorio** de Visual Studio para Mac, siga los pasos de la sección [Configuración de un repositorio de Subversion](~/set-up-subversion-repository.md).

## <a name="update-solution"></a>Actualizar solución

Cuando se usa un repositorio remoto, es importante recordar que otros usuarios pueden estar modificando archivos, lo que convertiría en obsoleta la copia de trabajo. Para evitarlo, siempre se recomienda incorporar los cambios desde el repositorio en la solución antes de empezar a trabajar y antes de confirmar. Para ello, seleccione el elemento de menú *Control de versiones > Actualizar solución*.

## <a name="review-solution-and-commit"></a>Revisar solución y confirmar

Para revisar los cambios en los archivos, use las pestañas Cambios, Culpar, Registro y Combinar de cada documento, como se muestra a continuación:

![Pestañas de Control de versiones](media/version-control-vcTabs.png)

Revise todos los cambios de un proyecto al ir al elemento de menú **Control de versiones > Revisar solución y confirmar**:

![Revisar solución](media/version-control-vcStatus.png)

Esto permite ver todos los cambios de cada archivo de un proyecto con la opción Revertir, Crear revisión o Confirmar.

Para confirmar un archivo en el repositorio remoto, haga clic en Confirmar..., escriba un mensaje de confirmación y confirme con el botón Confirmar:


![Confirmación de un archivo](media/version-control-svnCommit.png)

Con esto se envían los cambios al repositorio, donde crean la nueva revisión de todas las modificaciones.
