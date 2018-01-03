---
title: "Extensión de Excel de muestra: clases de elementos | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c251098-00aa-49cf-9e37-5717c0c6b3f1
caps.latest.revision: "9"
ms.author: douge
manager: douge
ms.workload: multiple
ms.openlocfilehash: 0a0643f6e290d5be5b4d2854246d5dc95c0d731f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="sample-excel-extension-element-classes"></a>Extensión de Excel de muestra: clases de elementos
La extensión usa clases que derivan de <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> y representan el control de la hoja de cálculo y el control de la celda en [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)].  
  
 El elemento base para esta extensión es el `ExcelElement`. Las clases `ExcelWorksheetElement` y `ExcelCellElement` se heredan de ese elemento  
  
## <a name="element-and-elementinformation-classes"></a>Element y ElementInformation (Clases)  
 `Element` es la clase base para todos los elementos de interfaz de usuario para la extensión de Excel, y hereda de la clase <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>. `ElementInformation` es la clase base para las clases de información de elemento en el ejemplo y no tiene miembros.  
  
#### <a name="simple-properties-and-methods"></a>Propiedades y métodos simples  
 Estos miembros devuelven valores simples, como el valor de la propiedad `Name` o el valor de la propiedad `ClassName` y el código es claro y fácil de leer. Algunos valores se devuelven mediante la clase `Utility`, que se explica más adelante. Otros devuelven `null` porque no son importantes en esta extensión del ejemplo. Hay dos miembros más interesantes que los demás: la propiedad <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A> y el método <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.CacheProperties%2A>.  
  
#### <a name="queryid-property"></a>Propiedad QueryId  
 Esta propiedad devuelve una condición que está formada por pares nombre-valor de propiedades que identifican de forma única el control durante la reproducción. Para cada clase de control derivada, el desarrollador debe invalidar esta propiedad para devolver un objeto <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement> que puede usar el marco para encontrar el control en la interfaz de usuario.  
  
#### <a name="cacheproperties-method"></a>CacheProperties (Método)  
 El marco de pruebas llama a este método durante el proceso de grabación para indicar al elemento que guarde una instantánea de las propiedades importantes. Esto mantiene las propiedades disponibles incluso cuando el control real de la interfaz de usuario ya no está en la pantalla.  
  
## <a name="worksheetelement-and-worksheetinformation-classes"></a>WorksheetInformation y WorksheetElement (Clases)  
 El clase `WorksheetElement` representa una hoja de cálculo de Excel en el marco de pruebas y se hereda de la clase base `Element`. Tres propiedades se invalidan para proporcionar información concreta sobre el objeto de hoja de cálculo de Excel: <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.ClassName%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.ControlTypeName%2A> y <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.Name%2A>.  
  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute> también se aplica en esta clase para que sea visible en COM.  
  
 La clase `WorksheetInformation` representa información sobre una hoja de cálculo de Excel. Tiene sólo un miembro, la propiedad `SheetName`, que es suficiente para este ejemplo.  
  
## <a name="cellelement-and-cellinformation-classes"></a>CellInformation y CellElement (Clases)  
 La clase `CellElement` representa una celda de Excel y se hereda de la clase base `Element`. El único miembro invalidado es la propiedad <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A>, que devuelve <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement> que usa las propiedades `RowIndex` y `ColumnIndex` para identificar la celda.  
  
## <a name="utilities-and-excelutilities-classes"></a>ExcelUtilities y Utilities (Clases)  
 La clase `ExcelUtilities` proporciona algunos valores constantes, como el nombre de la tecnología y un método que determina si el identificador de ventana proporcionado representa una hoja de cálculo de Excel.  
  
 La clase `Utilities` tiene métodos auxiliares que devuelven una gran variedad de información acerca de la interfaz de usuario. Algunos métodos utilizan llamadas directas a DLL externos del sistema, como **USER32. DLL** y **OLEACC. DLL**, para obtener los identificadores de ventana de la interfaz de usuario**.**  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement>   
 [Extender las pruebas de IU codificadas y las grabaciones de acciones para la compatibilidad con Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
