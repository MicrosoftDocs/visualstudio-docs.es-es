---
title: Información general de Visual Studio Tools para Unity | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-unity-tools
ms.topic: overview
ms.assetid: b4231bb9-45c4-4c77-ac3c-d05033b26393
caps.latest.revision: 6
ms.author: crdun
manager: crdun
ms.openlocfilehash: 69b9fb9bd21ad19199e5ba268c8f0a87fb546d57
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54776516"
---
# <a name="overview-of-visual-studio-tools-for-unity"></a>Información general de Visual Studio Tools para Unity
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
En esta sección aprenderá más acerca de las características que ofrece Visual Studio Tools para Unity y cómo utilizarlas para ser más productivo con Unity.  
  
 Con Visual Studio Tools para Unity (*VSTU*), puede usar Visual Studio para escribir scripts de editor y juegos en C# y, después, usar su eficaz depurador para buscar y corregir errores. La versión más reciente de VSTU incluye color de sintaxis para el lenguaje del sombreador de ShaderLab de Unity, visualizaciones mejoradas del depurador y generación de código mejorada para el Asistente de MonoBehavior. VSTU también integra los archivos de proyecto de Unity, los mensajes de la consola y la capacidad de iniciar el juego en Visual Studio, de modo que pueda dedicar menos tiempo a conmutar con el editor de Unity al escribir código.  
  
 Siga leyendo para obtener más información acerca de estas características.  
  
## <a name="integration-with-unity"></a>Integración con Unity  
 Visual Studio Tools para Unity no le permitiría aumentar su productividad si tuviera que alternar continuamente entre el editor de Unity y Visual Studio. Por eso Visual Studio Tools para Unity hace que resulte fácil seguir trabajando sin tener que salir de Visual Studio.  
  
-   El **Explorador de proyectos de Unity** muestra todo el proyecto de Unity dentro de Visual Studio con la misma jerarquía que se muestra en el editor de Unity.  
  
-   La integración con la consola de Unity muestra los resultados de la consola de Unity justo dentro de la ventana de errores de Visual Studio.  
  
-   Inicie la depuración del juego desde Visual Studio, sin necesidad de volver a Unity; tan solo tiene que presionar F5.  
  
## <a name="superior-debugging"></a>Depuración superior  
 Conecte el potente depurador de Visual Studio a su juego Unity para depurar sus archivos DLL y scripts de C# sin tener en cuenta si se está ejecutando de forma independiente o en el editor de Unity. Puede usar todas las características de depuración que espera de Visual Studio.  
  
- Puntos de interrupción, incluidos los puntos de interrupción condicionales.  
  
- Evalúe las expresiones complejas en la ventana Inspección.  
  
- Inspeccione y modifique el valor de variables y argumentos.  
  
- Profundice en complejas estructuras de datos y objetos.  
  
  Incluso puede depurar su juego Unity mientras se ejecuta en otro equipo de la red.  
  
## <a name="productivity"></a>Productividad  
 Además de la reconocida productividad de Visual Studio para escribir y refactorizar código en C#, Visual Studio Tools para Unity proporciona características de productividad adicionales para desarrolladores de Unity.  
  
-   Los colores de la sintaxis del lenguaje ShaderLab de Unity le ayudan a detectar errores en los sombreadores antes de que se conviertan en errores de programación. Tan solo tiene que abrir los archivos de ShaderLab en Visual Studio.  
  
-   El asistente de MonoBehavior le permite examinar una lista de comportamientos de Unity y crea código reutilizable para comportamientos con los que podría no estar familiarizado. Presione CTRL+MAYÚS+M.  
  
-   Una vez que esté familiarizado con los comportamientos de Unity que más utilice, el asistente rápido de MonoBehavior los pone al alcance de su mano. Presione CTRL+ALT+Q.  
  
-   Obtenga acceso a la documentación de Unity desde Visual Studio. Simplemente resalte la llamada API sobre la que quiera obtener información y, después, presione CTRL+ALT+M, CTRL+H.  
  
-   Acceda a todas estas características y a mucho más mediante métodos abreviados de teclado.  
  
## <a name="visual-studio-tools-for-unity-api"></a>API de Visual Studio Tools para Unity  
 Personalice y extienda el comportamiento de Visual Studio Tools para Unity mediante las API proporcionadas.  
  
-   Visual Studio Tools para Unity registra una devolución de llamada de registro para poder transmitir la consola de Unity a Visual Studio. Si tiene scripts de editor que registren la información, puede conectarlos en la misma devolución de llamada para enviar mensajes a Visual Studio. Para obtener más información, vea el siguiente ejemplo de Devolución de llamada de registro.  
  
-   Puede cambiar cómo Visual Studio Tools para Unity genera los archivos de proyecto usando la devolución de llamada de estilo de Unity ProjectFileGeneration. Para obtener más información, vea el ejemplo de Generación de archivos de proyecto.  
  
## <a name="see-also"></a>Vea también  
 [Página principal de Unity](http://unity3d.com)
