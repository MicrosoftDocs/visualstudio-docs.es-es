---
title: 'Extensión de Excel: PropertyProvider (clase) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 075d9b8d-8658-4fca-8711-08304dbac1c5
caps.latest.revision: 11
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d38b430dd88eb1a732c4e4ca335a0a5bb057b1f4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54801255"
---
# <a name="sample-excel-extension-propertyprovider-class"></a>Extensión de Excel: PropertyProvider (Clase)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esta clase interna extiende la clase <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> y proporciona servicios de propiedad para elementos [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] para grabar y reproducir pruebas de interfaz de usuario (IU).  
  
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
