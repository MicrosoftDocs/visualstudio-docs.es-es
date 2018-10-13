---
title: 'Extensión de Excel de muestra: TechnologyManager (Clase) | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8a7b760d-b5ac-4451-9593-6ac1a0b95cdb
caps.latest.revision: 11
ms.author: gewarren
manager: douge
ms.openlocfilehash: b23c3e735aba74d86b31afb4b83862d83bcd2bdb
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49190585"
---
# <a name="sample-excel-extension-technologymanager-class"></a>Extensión de Excel de muestra: TechnologyManager (Clase)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esta clase extiende la clase <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager> y es responsable de proporcionar servicios principales a la extensión [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)]. Aunque la clase base tiene muchos métodos, solo un subconjunto de ellos se utiliza en este ejemplo.  
  
 Algunos métodos simplemente devuelvan un valor de propiedad. Muchos de los métodos están diseñados para permitir que el programador invalide algoritmos predeterminados que se basan en el motor de pruebas de IU codificado. Estos métodos inician una <xref:System.NotSupportedException> o devuelven `null`, que indica el marco de trabajo para usar el algoritmo predeterminado.  
  
 Según la complejidad de la tecnología subyacente, desarrollar el código del administrador de tecnología puede llevar de varias semanas a unos meses. Excel proporciona una oportunidad para crear un administrador de tecnología potencialmente muy extenso. Este ejemplo se limita deliberadamente a las celdas y hojas de cálculo de Excel y utiliza un formato limitado.  
  
 Cuando es posible, el código del administrador de tecnología utiliza el canal de .NET Remoting abierto por la clase `Communicator` para extraer información desde el complemento en ejecución en el proceso de Excel.  
  
## <a name="com-visibility"></a>Visibilidad de COM  
 Tenga en cuenta que esta clase y cada clase de elemento que extiende la clase <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> tienen <xref:System.Runtime.InteropServices.ComVisibleAttribute> con un valor `true` para garantizar que las clases son visibles en COM.  
  
## <a name="technologyname-property"></a>TechnologyName (Propiedad)  
 Esta invalidación de la propiedad <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.TechnologyName%2A?displayProperty=fullName> debe proporcionar un nombre único y significativo que identifique la tecnología subyacente para cada componente de la extensión. Para esta extensión, el valor es "Excel".  
  
## <a name="getcontrolsupportlevel-method"></a>GetControlSupportLevel (Método)  
 Esta invalidación del método <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetControlSupportLevel%2A?displayProperty=fullName> devuelve un número que indica el nivel de compatibilidad que el administrador de tecnología puede ofrecer al control representado mediante el controlador proporcionado. Cuanto mayor sea el valor devuelto, mayor será la capacidad de admisión del administrador de tecnología del control. En este caso, el método comprueba la ventana que contiene el control y si es una hoja de cálculo de Excel, el método devuelve el valor más alto, de lo contrario, devuelve cero, lo que indica que no es compatible.  
  
## <a name="methods-to-get-an-element"></a>Métodos para obtener un elemento  
 Hay varios métodos importantes que usa el marco de pruebas de IU codificadas para obtener un elemento específico de la tecnología proporcionando un identificador, un punto de la pantalla o un elemento de una tecnología distinta. El código para estos métodos es autoexplicativo. Los métodos base son los siguientes:  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetFocusedElement%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromPoint%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromWindowHandle%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromNativeElement%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.ConvertToThisTechnology%2A?displayProperty=fullName>  
  
## <a name="parsequeryid-method"></a>ParseQueryId (Método)  
 Cuando se crea una prueba de IU codificada, el usuario puede especificar valores de propiedad de algunos o todos los controles en la prueba. El marco de pruebas utiliza estos valores de propiedad para crear pares de nombre-valor denominados propiedades de búsqueda que se usan para buscar los controles de interfaz de usuario específicos durante la prueba. Todas las propiedades de búsqueda representan conjuntamente el valor de la propiedad <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A?displayProperty=fullName> de cada elemento de la tecnología, que incluye cada control. Dado que un control podría tener que encontrarse varias veces durante una prueba, este método proporciona al administrador de tecnología una manera de optimizar el análisis de propiedades de búsqueda para el control dado. Este método también devuelve una cookie que el marco puede utilizar para las búsquedas posteriores de ese control. Esta implementación del método usa el método <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.AndCondition.Match%2A?displayProperty=fullName> para analizar las propiedades de búsqueda.  
  
## <a name="matchelement-method"></a>MatchElement (Método)  
 Para realizar una búsqueda de control por el administrador de tecnología, puede implementar el método <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.Search%2A?displayProperty=fullName> para devolver una matriz de posibles coincidencias o generar <xref:System.NotSupportedException>, que indica al marco que use su propio algoritmo de búsqueda. De cualquier manera, debe implementar el método <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.MatchElement%2A> donde esta implementación use de nuevo el método <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.AndCondition.Match%2A?displayProperty=fullName>.  
  
## <a name="navigation-methods"></a>Métodos de navegación  
 Estos métodos reciben el elemento primario, los elementos secundarios o elementos del mismo nivel del elemento proporcionado de la jerarquía de la interfaz de usuario. El código es simple y está comentado claramente.  
  
## <a name="getexcelelement-internal-method"></a>Método interno de GetExcelElement  
 Este método interno toma un identificador de ventana y la información sobre un elemento de Excel y devuelve el elemento de Excel solicitado.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager>   
 <xref:System.NotSupportedException>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>   
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A>   
 [Extender las pruebas de IU codificadas y las grabaciones de acciones para la compatibilidad con Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)



