---
title: "Extensi&#243;n de Excel de muestra: TechnologyManager (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8a7b760d-b5ac-4451-9593-6ac1a0b95cdb
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "mlearned"
manager: "douge"
---
# Extensi&#243;n de Excel de muestra: TechnologyManager (Clase)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta clase extiende la clase <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager> y es responsable de proporcionar los servicios principales para la extensión [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)].  Aunque la clase base tiene muchos métodos, en este ejemplo solo se usa un subconjunto de ellos.  
  
 Algunos métodos simplemente devuelven un valor de propiedad.  Muchos de los métodos están pensados para permitir al desarrollador invalidar algoritmos predeterminados integrados en el motor de pruebas de IU codificadas.  Estos métodos producen una excepción <xref:System.NotSupportedException> o devuelven `null`, que indica al marco que debe usar el algoritmo predeterminado.  
  
 Dependiendo de la complejidad de la tecnología subyacente, el desarrollo del código del administrador de tecnología puede durar desde unas semanas hasta unos meses.  Excel ofrece la posibilidad de crear un administrador de tecnología muy completo.  Este ejemplo está limitado intencionadamente a hojas de cálculo y celdas de Excel, y usa formato limitado.  
  
 Cuando es posible, el código del administrador de tecnología usa el canal .NET Remoting abierto por la clase `Communicator` para extraer información del complemento que se ejecuta en el proceso de Excel.  
  
## Visibilidad COM  
 Tenga en cuenta que esta clase y cada una de las clases de elemento que extienden la clase <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> tienen todas <xref:System.Runtime.InteropServices.ComVisibleAttribute> con un valor de `true` para asegurarse de que las clases son visibles para COM.  
  
## TechnologyName \(propiedad\)  
 Esta invalidación de la propiedad <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.TechnologyName%2A?displayProperty=fullName> debe proporcionar un nombre único y significativo que identifique la tecnología subyacente para todos los demás componentes de la extensión.  Para esta extensión, el valor es "Excel".  
  
## Método GetControlSupportLevel  
 Esta invalidación del método <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetControlSupportLevel%2A?displayProperty=fullName> devuelve un número que indica el nivel de compatibilidad que el administrador de tecnología puede ofrecer para el control representado por el identificador proporcionado.  Cuanto mayor sea el valor devuelto, mejor puede admitir el control el administrador de tecnología.  En este caso, el método comprueba la ventana que contiene el control y, si es una hoja de cálculo de Excel, el método devuelve el valor máximo; de lo contrario, devuelve cero, lo que indica que no se proporciona ninguna compatibilidad.  
  
## Métodos para obtener un elemento  
 El marco de pruebas de IU codificadas emplea varios métodos importantes para obtener un elemento específico de la tecnología proporcionando un controlador, un punto de la pantalla o un elemento de una tecnología diferente.  El código para estos métodos es autoexplicativo.  Los métodos base son los siguientes:  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetFocusedElement%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromPoint%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromWindowHandle%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromNativeElement%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.ConvertToThisTechnology%2A?displayProperty=fullName>  
  
## ParseQueryId \(método\)  
 Cuando se crea una prueba de IU codificada, el usuario puede especificar valores de propiedad para algunos o todos los controles de la prueba.  El marco de prueba usa estos valores de propiedad para crear pares de nombre y valor denominados propiedades de búsqueda que se emplean para encontrar determinados controles de la interfaz de usuario durante la prueba.  Todas las propiedades de búsqueda representan conjuntamente el valor de la propiedad <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A?displayProperty=fullName> de cada elemento de la tecnología, lo que incluye cada control.  Puesto que quizás haya que buscar un control varias veces durante una prueba, este método ofrece al administrador de tecnología una manera de optimizar el análisis de las propiedades de búsqueda para el control determinado.  Este método también devuelve una cookie que el marco puede usar para las búsquedas posteriores de ese control.  Esta implementación del método usa el método <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.AndCondition.Match%2A?displayProperty=fullName> para analizar las propiedades de búsqueda.  
  
## MatchElement \(método\)  
 Para que el administrador de tecnología busque un control, puede implementar el método <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.Search%2A?displayProperty=fullName> para devolver una matriz de posibles coincidencias u o producir la excepción <xref:System.NotSupportedException>, que indica al marco que debe usar su propio algoritmo de búsqueda.  En cualquier caso, debe implementar el método <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.MatchElement%2A> donde esta implementación usa de nuevo el método <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.AndCondition.Match%2A?displayProperty=fullName>.  
  
## Métodos de navegación  
 Estos métodos obtienen el elemento primario, los elementos secundarios o los elementos del mismo nivel del elemento proporcionado de la jerarquía de la interfaz de usuario.  El código es sencillo y comentado claramente.  
  
## GetExcelElement \(método interno\)  
 Este método interno toma un identificador de ventana e información sobre un elemento de Excel y devuelve el elemento de Excel solicitado.  
  
## Vea también  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager>   
 <xref:System.NotSupportedException>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>   
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A>   
 [Extender las pruebas de IU codificadas y las grabaciones de acciones para la compatibilidad con Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)