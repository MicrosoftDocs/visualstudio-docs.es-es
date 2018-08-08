---
title: 'Cómo: Abrir varias soluciones'
description: Obtenga información para abrir más de una solución en Visual Studio para Mac y para abrir más de una instancia de la aplicación.
author: asb3993
ms.author: amburns
ms.date: 07/19/2018
ms.assetid: 592BA4E3-8DEF-4FCD-8BA0-519A4CEEE03E
ms.openlocfilehash: 85d300c5131dad2d6f4480fceb4770e2e8a126a5
ms.sourcegitcommit: b544e2157ac20866baf158eef9cfed3e3f1d68b9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2018
ms.locfileid: "39388497"
---
# <a name="opening-multiple-solutions-or-instances-of-visual-studio-for-mac"></a>Apertura de varias soluciones o instancias de Visual Studio para Mac

De forma predeterminada, todas las aplicaciones de un equipo Mac, incluido Visual Studio para Mac, son aplicaciones de _instancia única_. Esto significa que si la aplicación que quiere usar ya está abierta (lo que se indica mediante un "punto" debajo del icono en la base), al hacer clic de nuevo en el icono se abre la instancia en ejecución, en lugar de una nueva.  Si necesita otras instancias de la aplicación, puede pedir al sistema que la abra, como se explica en la [siguiente sección](#open-a-second-instance-of-visual-studio-for-mac).

Además, al abrir una solución, el comportamiento predeterminado es abrirla en una nueva área de trabajo y cerrar el área de trabajo actual (si fuera necesario). Puede invalidar este comportamiento predeterminado si mantiene abierta el área de trabajo actual, como se explica en la sección [Abrir una segunda solución](#open-a-second-solution-inside-a-single-instance).

## <a name="open-a-second-instance-of-visual-studio-for-mac"></a>Abrir una segunda instancia de Visual Studio para Mac

Para abrir una segunda instancia del IDE, abra la aplicación **Terminal** y escriba la siguiente línea:

```bash
open -n "/Applications/Visual Studio.app"
```

## <a name="open-a-second-solution-inside-a-single-instance"></a>Apertura de una segunda solución dentro de una instancia única

Para abrir una segunda solución junto con la primera solución, siga estos pasos:

1. Con la primera solución ya abierta, seleccione **Archivo > Abrir**.
2. Examine el sistema de archivos para encontrar la solución existente.
3. Seleccione el archivo **.sln** y presione el botón **Opciones**:
    
    ![Ubicación del botón Opciones](media/open-multiple-solutions-image3.png)
4. Desactive la casilla **Cerrar área de trabajo actual**:

    ![Captura de pantalla del área de trabajo actual](media/open-multiple-solutions-image1.png)

1. Presione el botón Abrir para abrir la segunda solución en el Panel de solución.

**O bien**, si recientemente ha abierto la solución, puede usar los pasos siguientes:

1. Vaya al elemento de menú Archivo > Soluciones recientes:

    ![Captura de pantalla del menú Soluciones recientes](media/open-multiple-solutions-image2.png)

1. Mantenga presionada la tecla **Ctrl** y seleccione la solución. Esta combinación abre la segunda solución en el Panel de solución.
