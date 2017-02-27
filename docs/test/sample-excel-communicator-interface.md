---
title: "Interfaz de muestra del Communicator de Excel | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1dbf1090-762c-4824-82dd-2d7c2c6f00b6
caps.latest.revision: 11
ms.author: "mlearned"
manager: "douge"
caps.handback.revision: 11
---
# Interfaz de muestra del Communicator de Excel
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La interfaz `IExcelUICommunication` de ejemplo se utiliza en el objeto `ExcelUICommunicator` del proyecto `ExcelAddIn`.  
  
## Interfaz IExcelUICommunication  
 Esta interfaz define los puntos de comunicación entre `CodedUIExtension`, que se ejecuta en el proceso Prueba de IU codificada, y `ExcelCodedUIAddIn`, que se ejecuta en el proceso [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)].  
  
 El ensamblado `ExcelCodedUIAddinHelper` tiene una clase `ExcelUICommunicator` que deriva de esta interfaz y utiliza el modelo de objetos de Excel para procesar los métodos.  
  
 Algunos métodos reciben la información solicitada de Excel y después crean y devuelven uno de los objetos de información, como el objeto `CellInformation`.  
  
 Otros métodos utilizan un objeto de información proporcionado, encuentran el control correspondiente en Excel y hacen algún proceso en el control.  Por ejemplo, el método `ScrollIntoView` desplaza la hoja de cálculo para que la celda designada esté visible.  
  
## Comunicación de CodedUIExtensibilitySample y ExcelCodedUIAddinHelper  
 El ensamblado `ExcelCodedUIAddinHelper` se ejecuta en el proceso de Excel y tiene la clase `UICommunicator` que implementa la interfaz `IExcelUITestCommunication` y obtiene o establece la información necesaria de la Interfaz de usuario de Excel directamente.  
  
 El ensamblado `CodedUIExtensibilitySample` se ejecuta en el proceso de prueba de IU codificada de Visual Studio.  Este ensamblado tiene la clase `Communicator` que abre un canal de .NET Remoting y proporciona una propiedad `Instance` que usa la interfaz `IExcelUICommunication` para utilizar el objeto `UICommunicator` en el ensamblado `ExcelCodedUIAddinHelper` para pasar la solicitud y objetos de información, como un objeto `CellInformation`, entre los dos ensamblados.  
  
## Vea también  
 [Extender las pruebas de IU codificadas y las grabaciones de acciones para la compatibilidad con Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)   
 [Complemento de Excel de muestra para probar la IU codificada](../test/sample-excel-add-in-for-coded-ui-testing.md)   
 [Extensión de muestra para probar la IU codificada para Excel](../test/sample-coded-ui-test-extension-for-excel.md)