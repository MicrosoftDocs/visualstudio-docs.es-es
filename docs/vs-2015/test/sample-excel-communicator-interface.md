---
title: Interfaz de muestra del Communicator de Excel | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 1dbf1090-762c-4824-82dd-2d7c2c6f00b6
caps.latest.revision: 13
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 42da15899bb9bab6388d32c87132796eff768d7e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68158179"
---
# <a name="sample-excel-communicator-interface"></a>Interfaz de muestra del Communicator de Excel
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La interfaz de `IExcelUICommunication` de ejemplo se utiliza en el objeto `ExcelUICommunicator` y el proyecto `ExcelAddIn`.  
  
## <a name="iexceluicommunication-interface"></a>Interfaz IExcelUICommunication  
 Esta interfaz define los puntos de comunicación entre el `CodedUIExtension`, que se ejecuta en el proceso de prueba de IU codificada, y el `ExcelCodedUIAddIn`, que se ejecuta en el proceso [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)].  
  
 El ensamblado `ExcelCodedUIAddinHelper` tiene una clase `ExcelUICommunicator` que deriva de esta interfaz y utiliza el modelo de objetos de Excel para procesar los métodos.  
  
 Algunos métodos obtienen la información solicitada desde Excel y después crean y devuelven uno de los objetos de información, como el objeto `CellInformation`.  
  
 Otros métodos usan un objeto de información proporcionada, buscan el control correspondiente en Excel y realizan algún proceso en el control. Por ejemplo, el método `ScrollIntoView` desplaza la hoja de cálculo para que esté visible la celda designada.  
  
## <a name="codeduiextensibilitysample-and-excelcodeduiaddinhelper-communication"></a>Comunicación de CodedUIExtensibilitySample y ExcelCodedUIAddinHelper  
 El ensamblado `ExcelCodedUIAddinHelper` se ejecuta en el proceso de Excel y tiene la clase `UICommunicator` que implementa la interfaz `IExcelUITestCommunication` y obtiene o establece la información necesaria directamente desde la interfaz de usuario de Excel.  
  
 El ensamblado `CodedUIExtensibilitySample` se ejecuta en el proceso de prueba de IU codificada de Visual Studio. Este ensamblado tiene la clase `Communicator` que abre un canal de.NET Remoting y proporciona una propiedad `Instance` que usa la interfaz `IExcelUICommunication` para utilizar el objeto `UICommunicator` en el ensamblado `ExcelCodedUIAddinHelper` para pasar solicitudes y objetos de información, como un objeto `CellInformation` entre los dos ensamblados.  
  
## <a name="see-also"></a>Vea también  
 [Extender las pruebas de IU codificadas y las grabaciones de acciones para la compatibilidad con Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)   
 [Complemento de Excel de muestra para probar la IU codificada](../test/sample-excel-add-in-for-coded-ui-testing.md)   
 [Extensión de muestra para probar la IU codificada para Excel](../test/sample-coded-ui-test-extension-for-excel.md)
