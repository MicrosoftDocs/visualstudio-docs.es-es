---
title: "Extensi&#243;n de Excel de muestra: PropertyProvider (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 075d9b8d-8658-4fca-8711-08304dbac1c5
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "mlearned"
manager: "douge"
---
# Extensi&#243;n de Excel de muestra: PropertyProvider (Clase)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta clase interna extiende la clase <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> y proporciona los servicios de propiedad para los elementos de [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] para grabar y reproducir las pruebas de la interfaz de usuario.  
  
## Método GetControlSupportLevel  
 El método <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A> devuelve un número que indica el nivel de compatibilidad que el proveedor de propiedad puede proporcionar para el control.  Cuanto mayor sea el valor devuelto, mejor será la compatibilidad ofrecida.  En este caso, el método, comprueba el valor del campo de datos mediante el uso de la propiedad <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.TechnologyName%2A> del control proporcionado.  Si el valor es "Excel" y si <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.ControlTypeName%2A> indica que es `CellElement`, el método devuelve el valor máximo; de lo contrario, devuelve cero, que indica que no se proporciona compatibilidad.  
  
## GetPropertyNames \(método\)  
 Devuelve un diccionario de nombres y descriptores de propiedad para las propiedades compatibles de un control Excel Cell.  
  
## GetPropertyDescriptor \(método\)  
 El marco de prueba llama a este método para obtener el descriptor de propiedad predefinido para el nombre de propiedad proporcionada.  
  
## SetPropertyValue y GetPropertyValue \(métodos\)  
 El método `GetPropertyValue` utiliza la clase `Communicator` de esta extensión para devolver el valor de propiedad de Excel.  El método `SetPropertyValue` utiliza la clase <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard> y el componente `Communicator` para establecer el valor de propiedad.  El marco de prueba llama a estos métodos.  
  
## Métodos de personalización de generación de código  
 Estos métodos no se implementan para esta extensión.  Por consiguiente, devuelven `null` o producen <xref:System.NotImplementedException>.  
  
## Vea también  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard>   
 [Extender las pruebas de IU codificadas y las grabaciones de acciones para la compatibilidad con Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)