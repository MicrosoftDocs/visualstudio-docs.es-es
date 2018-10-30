---
title: Apertura de soluciones múltiples en Visual Studio para Mac
description: Obtenga información para abrir más de una solución en Visual Studio para Mac y para abrir más de una instancia de la aplicación.
author: conceptdev
ms.author: crdun
ms.date: 07/19/2018
ms.assetid: 592BA4E3-8DEF-4FCD-8BA0-519A4CEEE03E
ms.openlocfilehash: 4ffb7ce8a796641d54a5c29c58b9f166a9189d1c
ms.sourcegitcommit: 95aedf723c6be5272c3c5a2911cb2bdec50e2148
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/26/2018
ms.locfileid: "47228804"
---
# <a name="open-multiple-solutions-or-instances-of-visual-studio-for-mac"></a>Apertura de varias soluciones o instancias de Visual Studio para Mac

De forma predeterminada, todas las aplicaciones de un equipo Mac, incluido Visual Studio para Mac, son aplicaciones de _instancia única_. Esto significa que si la aplicación que quiere usar ya está abierta (lo que se indica mediante un punto debajo del icono en la base), al seleccionar de nuevo en el icono se abre la instancia en ejecución, en lugar de una nueva.  Si necesita otras instancias de la aplicación, puede pedir al sistema que la abra, como se explica en la [siguiente sección](#open-a-second-instance-of-visual-studio-for-mac).

Además, al abrir una solución, el comportamiento predeterminado es abrirla en una nueva área de trabajo y cerrar el área de trabajo actual (si fuera necesario). Puede invalidar este comportamiento predeterminado si mantiene abierta el área de trabajo actual, como se explica en la sección [Abrir una segunda solución](#open-a-second-solution-inside-a-single-instance).

## <a name="open-a-second-instance-of-visual-studio-for-mac"></a>Abrir una segunda instancia de Visual Studio para Mac

Para abrir una segunda instancia del entorno de desarrollo integrado (IDE), abra la aplicación **Terminal** y escriba la siguiente línea:

```bash
open -n "/Applications/Visual Studio.app"
```

## <a name="open-a-second-solution-inside-a-single-instance"></a>Apertura de una segunda solución dentro de una instancia única

Para abrir una segunda solución junto con la primera solución, siga estos pasos:

1. Con la primera solución ya abierta, seleccione **Archivo** > **Abrir**.
2. Examine el sistema de archivos para encontrar la solución existente.
3. Seleccione el archivo **.sln** y seleccione **Opciones**:
    
    ![Captura de pantalla de Visual Studio para Mac, con el archivo .sln y las opciones resaltadas](media/open-multiple-solutions-image3.png)
4. Desactive la casilla **Cerrar área de trabajo actual**:

    ![Captura de pantalla del cuadro de diálogo Opciones con el cuadro Cerrar de área de trabajo actual desactivado](media/open-multiple-solutions-image1.png)

1. Seleccione **Abrir** para abrir la segunda solución en el Panel de solución.

O bien, si recientemente ha abierto la solución, puede usar los pasos siguientes:

1. Vaya a **Archivo** > **Soluciones recientes**.

    ![Captura de pantalla del menú Soluciones recientes](media/open-multiple-solutions-image2.png)

1. Mantenga presionada la tecla **Ctrl** y seleccione la solución. Esta combinación abre la segunda solución en el Panel de solución.
