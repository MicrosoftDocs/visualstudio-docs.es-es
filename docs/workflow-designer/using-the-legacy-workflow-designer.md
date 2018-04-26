---
title: Usar el Diseñador de flujo de trabajo heredado
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- Visual Studio 2005 Extensions for Windows Workflow Foundation, about
ms.assetid: 7af53077-afd7-465f-9c1d-b387e9d4f216
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 794b52c918eb727fe67d24af209d21403da18475
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="using-the-legacy-workflow-designer"></a>Usar el Diseñador de flujo de trabajo heredado

Heredado proporcionados por el Diseñador de flujo de trabajo mediante Visual Studio 2010 puede utilizarse como destino la versión 3.5 de .NET Framework o el conocido como WinFX.

Se tiene acceso seleccionando la opción el **.NET Framework 3.0** opción o **.NET Framework 3.5** opción en la lista desplegable lista en la parte superior de la **nuevo proyecto** ventana. La opción predeterminada en Visual Studio 2010 es **.NET Framework 4** que se usa para crear aplicaciones de Windows Workflow Foundation (WF) que tienen como destino .NET Framework 4.

El Diseñador de flujo de trabajo proporciona una manera de crear gráficamente aplicaciones de Windows Workflow Foundation (WF) mediante la conocida interfaz de usuario de Visual Studio. Las aplicaciones de Windows Workflow Foundation (WF) se componen de pasos del proceso de flujo de trabajo denominados actividades. Para crear un flujo de trabajo, cree actividades en la superficie de diseño arrastrando sus diseñadores de actividad correspondientes desde **cuadro de herramientas** a la superficie de diseño.

En la tabla siguiente se enumera las características claves de Visual Studio para Windows Workflow Foundation.

|Característica|Descripción|
|-------------|-----------------|
|Arrastrar y colocar actividad|Arrastre las actividades desde el **cuadro de herramientas** a la superficie de diseño para crear un flujo de trabajo.|
|Examinador de propiedades|El estándar **propiedades** ventana de Visual Studio se utiliza para configurar las propiedades de una actividad.|
|Zoom|Los prismáticos **nivel de Zoom** se encuentra debajo de la barra de desplazamiento vertical en el lado derecho de la superficie de diseño. Haga clic en los prismáticos y seleccione un porcentaje de zoom para ampliar o reducir el gráfico del flujo de trabajo. También puede usar el **Pan** opciones de cursor de icono de lupa para acercar y alejar.|
|Movimiento panorámico|El **Pan** , un círculo con cuatro flechas cruzadas que señalan cuatro direcciones, que se encuentra debajo de la barra de desplazamiento vertical en el lado derecho de la superficie de diseño, debajo del icono de zoom de prismáticos. Si hace clic en el icono de panorámica, aparece un menú emergente con las opciones de cursor siguientes:<br /><br /> -El **acercar** cursor de lupa le permite acercar haciendo clic en la superficie de diseño.<br />-El **alejar** cursor de lupa le permite alejar haciendo clic en la superficie de diseño.<br />-El **herramienta de exploración** cursor de mano que le permite "agarrar" y desplazar la vista de un flujo de trabajo en la superficie de diseño.<br />-El **predeterminado** cursor de flecha permite cambiar de los demás cursores al cursor de flecha predeterminado.|
|Desplazamiento automático|Si tiene un flujo de trabajo grande, podría desear colocar una actividad más allá de la presentación visible del área de superficie de diseño. Visual Studio le permite arrastrar una actividad hacia el borde de la superficie de diseño más cercana a donde desea colocar la actividad. La vista de superficie de diseño se desplaza automáticamente en esa dirección.|
|Etiquetas inteligentes|Las actividades que no se configuran totalmente o cuya configuración no sea válida se marcan con un icono de signo de exclamación. Puede hacer clic en el icono y ver una lista desplegable con las necesidades de configuración de la actividad. A continuación, puede usar el **propiedades** ventana para configurar adecuadamente la actividad. Cuando todas las propiedades son válidas para la actividad, el icono de signo de exclamación desaparece.|

## <a name="see-also"></a>Vea también

- [Desarrollo de flujos de trabajo](http://go.microsoft.com/fwlink?LinkID=65010)