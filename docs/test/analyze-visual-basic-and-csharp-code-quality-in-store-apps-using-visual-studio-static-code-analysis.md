---
title: "Análisis de la calidad del código de Visual Basic y C# de las aplicaciones para UWP con el análisis de código estático de Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.propertypages.csvb.express
ms.assetid: cab553fc-19a9-4cbf-858e-8200258ffe50
caps.latest.revision: "14"
author: erickson-doug
ms.author: douge
manager: douge
ms.openlocfilehash: e61f307872f60da316480d3654507b5225588f41
ms.sourcegitcommit: c0422a3d594ea5ae8fc03f1aee684b04f417522e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/02/2017
---
# <a name="analyze-visual-basic-and-c-code-quality-in-uwp-apps-using-visual-studio-static-code-analysis"></a>Análisis de la calidad del código de Visual Basic y C# de las aplicaciones para UWP con el análisis de código estático de Visual Studio
![Se aplica a Windows y Windows Phone](../debugger/media/windows_and_phone_content.png "windows_and_phone_content")  
  
 La herramienta de análisis de código de Visual Studio Express examina el código para detectar una serie de defectos comunes e infracciones de las prácticas recomendadas de programación. Las advertencias del análisis de código son distintas de los errores y advertencias del compilador, porque la herramienta de análisis de código busca patrones de código concretos que, aunque son válidos, pueden crear problemas para ti o para otros usuarios del código. El análisis de código también puede encontrar defectos del código que son difíciles de detectar al hacer las pruebas. Ejecutar la herramienta de análisis de código a intervalos regulares durante el proceso de desarrollo puede mejorar la calidad de la aplicación final.  
  
> [!NOTE]
>  En Visual Studio Ultimate, Visual Studio Premium y Visual Studio Professional, puedes usar la funcionalidad completa de análisis de código. Consulte [Analizar la calidad de la aplicación mediante herramientas de análisis del código](http://msdn.microsoft.com/library/dd264897.aspx) en la MSDN Library.  
  
## <a name="in-this-topic"></a>En este tema  
 Puedes obtener información sobre:  
  
 [Ejecutar análisis de código](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Run)  
  
 [Analizar y resolver advertencias del análisis de código](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Analyze)  
  
 [Suprimir las advertencias de análisis de código](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Suppress)  
  
 [Buscar y filtrar resultados del análisis de código](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Search)  
  
 [Advertencias de análisis de código de Visual Basic y C#](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Warnings)  
  
##  <a name="BKMK_Run"></a> Ejecutar análisis de código  
 Para ejecutar un análisis de código en la solución de Visual Studio:  
  
-   En el menú **Compilar**, elija **Ejecutar análisis de código en la solución**.  
  
 Para ejecutar automáticamente el análisis de código cada vez que compiles un proyecto:  
  
1.  Haga clic con el botón derecho en el nombre del proyecto en el Explorador de soluciones y seleccione **Propiedades**.  
  
2.  En la página de propiedades del proyecto, elija **Análisis de código** y, después, **Habilitar análisis de código al compilar (define la constante CODE_ANALYSIS)**.  
  
 Se compila la solución y se ejecuta el análisis de código. Los resultados aparecen en la ventana Análisis de código.  
  
 ![Ventana Análisis de código](../test/media/ca_managed_collapsed.png "CA_Managed_Collapsed")  
  
##  <a name="BKMK_Analyze"></a> Analizar y resolver advertencias del análisis de código  
 Para analizar una advertencia concreta, haz clic en su título en la ventana Análisis de código. La advertencia se expande para mostrar información detallada sobre el problema.  
  
 ![Advertencia de análisis de código expandida](../test/media/ca_managed_callouts.png "CA_Managed_Callouts")  
  
 Cuando se expande una advertencia, la línea de código que ha causado la advertencia se resalta en el editor de código de Visual Studio.  
  
 ![Resaltado de texto de análisis de código](../test/media/ca_managed_sourceline.png "CA_Managed_SourceLine")  
  
 Cuando hayas entendido el problema, podrás resolverlo en el código. Después, ejecuta otra vez el análisis de código, para asegurarte de que no vuelve a aparecer en la ventana Análisis de código y de que la corrección no generó otras advertencias.  
  
> [!TIP]
>  Puedes repetir el análisis de código desde la ventana Análisis de código. Haga clic en el botón **Analizar** y seleccione el ámbito de análisis. Puedes repetir el análisis en toda la solución o en el proyecto seleccionado.  
  
##  <a name="BKMK_Suppress"></a> Suprimir las advertencias de análisis de código  
 A veces, uno decide no corregir una advertencia del análisis de código. Puede ser que para resolverla se necesita un esfuerzo de codificación excesivo en proporción con la probabilidad de que el problema surja en las implementaciones reales del código. O puede que consideres que el análisis que ha dado lugar a la advertencia no es apropiado para ese contexto concreto. Puedes suprimir advertencias individuales de modo que ya no aparezcan en la ventana Análisis de código.  
  
 Para suprimir una advertencia:  
  
1.  Si la información detallada no aparece, haz clic en el título de la advertencia para expandirla.  
  
2.  Elige el vínculo **Acciones** en la parte inferior de la advertencia.  
  
3.  Apunte a **Suprimir mensaje** y elija **En origen** o **En archivo de supresión**.  
  
    -   **En origen** inserta un atributo `SuppressMessage` en el archivo de origen antes del método que ha generado la advertencia. De esta forma, la supresión es más reconocible.  
  
    -   **En el archivo de supresión** agrega un atributo `SuppressMessage` al archivo **GlobalSuppressions.cs** del proyecto. Esto puede facilitar la administración de supresiones. Observe que el atributo `SuppressMessage` agregado a **GlobalSuppression.cs** también tiene como destino el método que ha generado la advertencia. No suprime la advertencia globalmente.  
  
     La decisión de suprimir la advertencia en el archivo de origen o en el archivo de supresión depende de tu estilo y tus necesidades de codificación.  
  
##  <a name="BKMK_Search"></a> Buscar y filtrar resultados del análisis de código  
 Puedes buscar en las listas largas de mensajes de advertencia y filtrar las advertencias en las soluciones de varios proyectos.  
  
 ![Buscar y filtrar la ventana de análisis de código](../test/media/ca_searchfilter.png "CA_SearchFilter")  
  
 En [!INCLUDE[vs_dev11_expwin_long](../misc/includes/vs_dev11_expwin_long_md.md)], todas las advertencias de análisis de código tienen el nivel de gravedad de advertencia.  
  
##  <a name="BKMK_Warnings"></a> Advertencias de análisis de código de Visual Basic y C#  
 El análisis de código produce las advertencias siguientes:  
  
 [CA1001: Los tipos que poseen campos descartables deben ser descartables](http://msdn.microsoft.com/library/ms182172.aspx)  
  
 [CA1821: Quitar los finalizadores vacíos](http://msdn.microsoft.com/library/bb264476.aspx)  
  
 [CA2213: Aplique Dispose a los campos a los que se pueda](http://msdn.microsoft.com/library/ms182328.aspx)  
  
 [CA2229: Implementar constructores de serialización](http://msdn.microsoft.com/library/ms182343.aspx)  
  
 [CA2231: Sobrecargar el operador equals al invalidar ValueType.Equals](http://msdn.microsoft.com/library/ms182359.aspx)
