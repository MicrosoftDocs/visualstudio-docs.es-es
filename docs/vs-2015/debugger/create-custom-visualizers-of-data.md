---
title: Crear visualizadores personalizados de datos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.visualizer.troubleshoot
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, visualizers
- visualizers
ms.assetid: c24c006f-f2ac-429f-89db-677fc0c6e1ea
caps.latest.revision: 31
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d8433af07b5f1315e73e6916e58123fcd14bddf0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51792865"
---
# <a name="create-custom-visualizers-of-data"></a>Crear visualizadores personalizados de datos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los visualizadores son componentes de la [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] interfaz de usuario del depurador. Un *visualizador* crea un cuadro de diálogo u otra interfaz para mostrar una variable o un objeto de forma que sea adecuada para su tipo de datos. Por ejemplo, un visualizador HTML interpreta una cadena HTML y muestra el resultado tal como aparecería en una ventana del explorador; un visualizador de mapa de bits interpreta una estructura de mapa de bits y muestra el gráfico que representa. Algunos visualizadores permiten modificar y ver los datos.  
  
 El depurador de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] incluye seis visualizadores estándar. Se trata el texto, HTML, XML y JSON visualizadores, todos ellos funcionan en objetos de cadena; el visualizador de árboles de WPF, para mostrar las propiedades de un árbol visual de objetos WPF; y el visualizador del conjunto de datos, que funciona con objetos DataSet, DataView y DataTable. Es posible que, en el futuro, haya visualizadores adicionales disponibles para descargar de Microsoft Corporation, de terceros y de la comunidad. También puede escribir sus propios visualizadores e instalarlos en el depurador de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].  
  
> [!NOTE]
>  En **Store** aplicaciones, sólo el texto estándar, se admiten los visualizadores HTML, XML y JSON. No se admiten los visualizadores personalizados (creados por el usuario).  
  
 Los visualizadores se representan en el depurador mediante un icono de lupa. Cuando vea el icono de lupa en una **información sobre datos**, en una ventana de variables del depurador o en el **Inspección rápida** cuadro de diálogo, puede hacer clic en el icono de lupa para seleccionar un visualizador adecuado para el tipo de datos del objeto correspondiente.  
  
 Los visualizadores no se admiten en .NET Compact Framework.  
  
> [!NOTE]
>  Los visualizadores del depurador requieren más privilegios de los permitidos por una aplicación de confianza parcial. Como resultado, los visualizadores no se cargarán cuando la ejecución se detenga en código con confianza parcial. Para depurar con un visualizador, debe ejecutar el código con plena confianza.  
  
## <a name="in-this-section"></a>En esta sección  
 [Cómo: Escribir un visualizador](../debugger/how-to-write-a-visualizer.md)  
  
 [Tutorial: Escribir un visualizador en C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)  
  
 [Cómo: Instalar un visualizador](../debugger/how-to-install-a-visualizer.md)  
  
 [Cómo: Comprobar y depurar un visualizador](../debugger/how-to-test-and-debug-a-visualizer.md)  
  
 [Referencia de la API del visualizador](../debugger/visualizer-api-reference.md)  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Ver datos en el depurador](../debugger/viewing-data-in-the-debugger.md)



