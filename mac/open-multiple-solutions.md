---
title: Procedimiento Abrir varias soluciones
description: Obtenga información para abrir más de una solución en Visual Studio para Mac y para abrir más de una instancia de la aplicación.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/09/2020
ms.assetid: 592BA4E3-8DEF-4FCD-8BA0-519A4CEEE03E
ms.custom: video
ms.topic: how-to
ms.openlocfilehash: e54f002141379d93a40df69ea070d5a64eba2f7d
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493444"
---
# <a name="open-multiple-solutions-or-instances-of-visual-studio-for-mac"></a>Apertura de varias soluciones o instancias de Visual Studio para Mac

De forma predeterminada, todas las aplicaciones de un equipo Mac, incluido Visual Studio para Mac, son aplicaciones de _instancia única_. Esto significa que si la aplicación que quiere usar ya está abierta (lo que se indica mediante un punto debajo del icono en la base), al seleccionar de nuevo el icono se abre la instancia en ejecución, en lugar de una nueva. Si necesita otras instancias de la aplicación, puede pedir al sistema que la abra, como se explica en la [siguiente sección](#open-a-second-instance-of-visual-studio-for-mac).

Además, al abrir una solución, el comportamiento predeterminado es abrirla en una nueva área de trabajo y cerrar el área de trabajo actual (si fuera necesario). Puede invalidar este comportamiento predeterminado si mantiene abierta el área de trabajo actual, como se explica en la sección [Abrir una segunda solución](#open-a-second-solution-inside-a-single-instance).

## <a name="open-a-second-instance-of-visual-studio-for-mac"></a>Abrir una segunda instancia de Visual Studio para Mac

Para abrir una segunda instancia del entorno de desarrollo integrado (IDE), haga clic con el botón derecho en el icono de Visual Studio en el dock o en la carpeta **Aplicaciones** y seleccione **Nueva instancia**.

![Captura de pantalla de la opción de menú Nueva instancia al hacer clic con el botón derecho en el icono de Visual Studio](media/open-new-instance.png)

## <a name="open-a-second-solution-inside-a-single-instance"></a>Apertura de una segunda solución dentro de una instancia única

Para abrir una segunda solución junto con la primera solución, siga estos pasos:

1. Con la primera solución ya abierta, seleccione **Archivo** > **Abrir**.
2. Examine el sistema de archivos para encontrar la solución existente.
3. Seleccione el archivo **.sln** y seleccione **Opciones**:

    ![Captura de pantalla de Visual Studio para Mac, con el archivo .sln y las opciones resaltadas](media/open-multiple-solutions-image3.png)

4. Desactive la casilla **Cerrar área de trabajo actual**:

    ![Captura de pantalla del cuadro de diálogo Opciones con el cuadro Cerrar de área de trabajo actual desactivado](media/open-multiple-solutions-image1.png)

5. Seleccione **Abrir** para abrir la segunda solución en la ventana de la solución.

O bien, si recientemente ha abierto la solución, puede usar los pasos siguientes:

1. Vaya a **Archivo** > **Soluciones recientes**.

    ![Captura de pantalla del menú Soluciones recientes](media/open-multiple-solutions-image2.png)

1. Mantenga presionada la tecla **Ctrl** y seleccione la solución. Esta combinación abre la segunda solución en la ventana de la solución.

## <a name="related-video"></a>Vídeo relacionado

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Work-With-Multiple-Solutions/player]
