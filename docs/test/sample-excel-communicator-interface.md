---
title: Interfaz de muestra del Communicator de Excel
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: sample
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 88aa282a2e742ffff53582fd4855d06e3a06db69
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="sample-excel-communicator-interface"></a>Interfaz de muestra del Communicator de Excel
La interfaz de `IExcelUICommunication` de ejemplo se utiliza en el objeto `ExcelUICommunicator` y el proyecto `ExcelAddIn`.

## <a name="iexceluicommunication-interface"></a>Interfaz IExcelUICommunication
 Esta interfaz define los puntos de comunicación entre el `CodedUIExtension`, que se ejecuta en el proceso de prueba de IU codificada, y el `ExcelCodedUIAddIn`, que se ejecuta en el proceso [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)].

 El ensamblado `ExcelCodedUIAddinHelper` tiene una clase `ExcelUICommunicator` que deriva de esta interfaz y utiliza el modelo de objetos de Excel para procesar los métodos.

 Algunos métodos obtienen la información solicitada desde Excel y después crean y devuelven uno de los objetos de información, como el objeto `CellInformation`.

 Otros métodos usan un objeto de información proporcionada, buscan el control correspondiente en Excel y realizan algún proceso en el control. Por ejemplo, el método `ScrollIntoView` desplaza la hoja de cálculo para que esté visible la celda designada.

## <a name="codeduiextensibilitysample-and-excelcodeduiaddinhelper-communication"></a>Comunicación de CodedUIExtensibilitySample y ExcelCodedUIAddinHelper
 El ensamblado `ExcelCodedUIAddinHelper` se ejecuta en el proceso de Excel y tiene la clase `UICommunicator` que implementa la interfaz `IExcelUITestCommunication` y obtiene o establece la información necesaria directamente desde la interfaz de usuario de Excel.

 El ensamblado `CodedUIExtensibilitySample` se ejecuta en el proceso de prueba de IU codificada de Visual Studio. Este ensamblado tiene la clase `Communicator` que abre un canal de.NET Remoting y proporciona una propiedad `Instance` que usa la interfaz `IExcelUICommunication` para utilizar el objeto `UICommunicator` en el ensamblado `ExcelCodedUIAddinHelper` para pasar solicitudes y objetos de información, como un objeto `CellInformation` entre los dos ensamblados.

## <a name="see-also"></a>Vea también

- [Extender las pruebas de IU codificadas y las grabaciones de acciones para la compatibilidad con Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
- [Complemento de Excel de muestra para probar la IU codificada](../test/sample-excel-add-in-for-coded-ui-testing.md)
- [Extensión de muestra para probar la IU codificada para Excel](../test/sample-coded-ui-test-extension-for-excel.md)
