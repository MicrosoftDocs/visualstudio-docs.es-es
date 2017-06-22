---
title: "Extensión de Excel de muestra: PropertyProvider (Clase) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 075d9b8d-8658-4fca-8711-08304dbac1c5
caps.latest.revision: 9
ms.author: douge
manager: douge
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ab78b6b8eaa8156ed2c8a807b1d8a80e75afa84
ms.openlocfilehash: 99397f8f0c6e0e261451cae642cf6e48fe5bba56
ms.contentlocale: es-es
ms.lasthandoff: 05/19/2017

---
# <a name="sample-excel-extension-propertyprovider-class"></a>Extensión de Excel de muestra: PropertyProvider (Clase)
Esta clase interna extiende la clase <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> y proporciona servicios de propiedad para elementos [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] para grabar y reproducir pruebas de interfaz de usuario (IU).  
  
## <a name="getcontrolsupportlevel-method"></a>GetControlSupportLevel (Método)  
 El método <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A> devuelve un número que indica el nivel de compatibilidad que el proveedor de propiedades puede ofrecer para el control proporcionado. Cuanto mayor sea el valor devuelto, mayor será la capacidad de admisión del proveedor de propiedad del control. En este caso, el método comprueba el valor de la propiedad <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.TechnologyName%2A> del control proporcionado. Si el valor es "Excel" y el <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.ControlTypeName%2A> indica que es un `CellElement`, el método devuelve el valor más alto, de lo contrario, devuelve cero, lo que indica que no son compatibles.  
  
## <a name="getpropertynames-method"></a>GetPropertyNames (Método)  
 Devuelve un diccionario de nombres de propiedad y descriptores de propiedad para las propiedades compatibles de un control de celda de Excel.  
  
## <a name="getpropertydescriptor-method"></a>GetPropertyDescriptor (Método)  
 El marco de pruebas llama a este método para obtener el descriptor de propiedad predefinido para el nombre de propiedad proporcionado.  
  
## <a name="getpropertyvalue-and-setpropertyvalue-methods"></a>GetPropertyValue y SetPropertyValue (Métodos)  
 El método `GetPropertyValue` usa la clase `Communicator` de esta extensión para devolver el valor de propiedad de Excel. El método `SetPropertyValue` usa la clase <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard> y el componente `Communicator` para establecer el valor de propiedad. El marco de pruebas llama a estos métodos.  
  
## <a name="code-generation-customization-methods"></a>Métodos de personalización de la generación de código  
 Estos métodos no se implementan para esta extensión. Por lo tanto, devuelven `null` o generan <xref:System.NotImplementedException>.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard>   
 [Extender las pruebas de IU codificadas y las grabaciones de acciones para la compatibilidad con Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)

