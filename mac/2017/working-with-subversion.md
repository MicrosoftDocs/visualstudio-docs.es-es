---
title: Trabajar con Subversion
description: Empleo de Subversion en Visual Studio para Mac.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 2400ED9C-6236-4C0A-A3AB-9D7CBE1F0CF4
ms.openlocfilehash: bd46a9eba7770b73425f1461fab6cb8443ace26c
ms.sourcegitcommit: 703c68667261df5985a73282c1cbb0541118989c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "89402275"
---
# <a name="working-with-subversion"></a>Trabajar con Subversion

Subversion es el sistema de control de versiones centralizado que permite extraer del repositorio una única copia principal de los datos centralizados. A diferencia de Git, la extracción de un repositorio de Subversion no clona la totalidad del repositorio, sino que solo toma una instantánea en ese momento dado.

Subversion usa un modelo Copiar-Modificar-Combinar para permitir que los usuarios trabajen simultáneamente en el mismo repositorio. Esto significa que cada usuario crea una copia local, o de trabajo, de los datos centralizados en la que luego puede trabajar de forma independiente. Los cambios en las copias de trabajo de los usuarios se combinan de forma cronológica.

Por ejemplo, imagine que el usuario A y el usuario B extraen una copia del repositorio remoto y cada uno modifica archivos. El usuario A termina las modificaciones y las confirma de forma remota. Antes de que el usuario B confirme su trabajo, tiene que actualizar su copia de trabajo con los cambios del repositorio remoto, es decir, mediante la combinación de los cambios del usuario A.

En las siguientes secciones se analiza cómo usar Subversion para el control de versiones en Visual Studio para Mac.

En la imagen siguiente se ven las opciones proporcionadas en el elemento de menú Control de versiones de Visual Studio para Mac:

![Elemento de menú Control de versiones](media/version-control-svnVersionControlMenu.png)

## <a name="checkout"></a>Extraer del repositorio...

Antes de empezar a usar un repositorio remoto de Subversion, extraiga el repositorio para crear una copia de trabajo de ese directorio en el equipo local.

Para obtener más información sobre el uso de la característica **Extraer del repositorio** de Visual Studio para Mac, siga los pasos de la sección [Configuración de un repositorio de Subversion](set-up-subversion-repository.md).

## <a name="update-solution"></a>Actualizar solución

Cuando se usa un repositorio remoto, es importante recordar que otros usuarios pueden estar modificando archivos, lo que convertiría en obsoleta la copia de trabajo. Para evitar los conflictos, siempre se recomienda incorporar los cambios desde el repositorio en la solución antes de empezar a trabajar y antes de confirmar. Para ello, seleccione el elemento de menú **Control de versiones > Actualizar solución**.

## <a name="review-solution-and-commit"></a>Revisar solución y confirmar

Para revisar los cambios en los archivos, use las pestañas Cambios, Culpar, Registro y Combinar de cada documento, como se muestra en la imagen siguiente:

![Pestañas de Control de versiones](media/version-control-vcTabs.png)

Revise todos los cambios de un proyecto al ir al elemento de menú **Control de versiones > Revisar solución y confirmar**:

![Revisar solución](media/version-control-vcStatus.png)

Esto permite ver todos los cambios de cada archivo de un proyecto con la opción Revertir, Crear revisión o Confirmar.

Para confirmar un archivo en el repositorio remoto, haga clic en Confirmar..., escriba un mensaje de confirmación y confirme con el botón Confirmar:

![Confirmación de un archivo](media/version-control-svnCommit.png)

Con esto se envían los cambios al repositorio, donde crean la nueva revisión de todas las modificaciones.

## <a name="see-also"></a>Consulte también

- [Configurar un repositorio de Subversion](set-up-subversion-repository.md)
