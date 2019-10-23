---
title: Actualización de una aplicación para UWP | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- JavaScript debugging, refreshing pages [UWP apps]
- debugging, refreshing pages [UWP apps]
- DOM Explorer, Refresh [UWP apps]
- Refresh [UWP apps]
ms.assetid: fd99ee60-fa94-46df-8b17-369f60bfd908
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- uwp
ms.openlocfilehash: 0b1d19c0b607d2c5a09fddc9d4550230e478d57a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72730307"
---
# <a name="refresh-a-uwp-app-in-visual-studio"></a>Actualizar una aplicación de UWP en Visual Studio

 Puede realizar cambios en el código durante la depuración y, después, actualizar una aplicación de UWP con JavaScript eligiendo el botón **Actualizar aplicación de Windows** en la barra de herramientas **depurar** . Al elegir este botón, se recarga la aplicación sin detener y reiniciar el depurador. La característica Actualizar te permite modificar código de HTML, CSS y JavaScript, y ver el resultado rápidamente. Esta característica es compatible con las aplicaciones UWP.

 La actualización no conserva el estado de la aplicación ni refleja los siguientes cambios en la aplicación:

- Cambios en el archivo de manifiesto del paquete, incluidos los cambios de imágenes especificadas en el manifiesto del paquete.

- Cambios de referencias, como agregar o quitar una referencia de SDK, o cambios a los componentes de Windows en tiempo de ejecución (archivos .winmd).

- Cambios de recursos, como los aplicados a cadenas de archivos .resjson.

- Cambios del archivo de proyecto que dan lugar a cambios del nombre de la ruta de acceso, nuevos archivos de proyecto o archivos eliminados.

- Cambios de propiedades del proyecto y de elementos, como cambios en el dispositivo de depuración seleccionado, o en la acción de empaquetado de un archivo (en la ventana Propiedades).

> [!IMPORTANT]
> Cuando cambias las referencias, cambias el manifiesto del paquete o realizas otros cambios especificados en la lista anterior, debes detener y reiniciar el depurador para actualizar los archivos de código fuente HTML, CSS y JavaScript.

### <a name="to-refresh-an-app"></a>Para actualizar una aplicación

1. Con el proyecto de UWP abierto en Visual Studio, seleccione **equipo local** como destino de depuración.

     ![Seleccionar lista de destinos de depuración](../debugger/media/js_select_target.png "JS_Select_Target")

3. Presiona F5 para ejecutar la aplicación en modo de depuración.

4. Cambia a Visual Studio.

5. En la Página principal de la aplicación de UWP, edite el código HTML.

7. Haga clic en el botón **Actualizar aplicación de Windows** , que tiene el siguiente aspecto: ![botón actualizar aplicación de Windows](../debugger/media/js_refresh.png "JS_Refresh"). (O bien, presiona F4).

8. Cambia a la aplicación. La aplicación se recarga y el HTML actualizado se usa para representar la aplicación.

## <a name="see-also"></a>Vea también
- [Inicio rápido: Depurar HTML y CSS](../debugger/quickstart-debug-html-and-css.md)