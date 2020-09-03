---
title: Interfaz de muestra del Communicator de Excel | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 1dbf1090-762c-4824-82dd-2d7c2c6f00b6
caps.latest.revision: 13
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3e3a9bd037c8886743910af649bf831b11337598
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660484"
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

## <a name="see-also"></a>Consulte también
 [Extender las pruebas de IU codificadas y las grabaciones de acciones para admitir](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md) [el complemento de Excel de ejemplo de Microsoft Excel para pruebas de IU](../test/sample-excel-add-in-for-coded-ui-testing.md) codificadas [ejemplo de la extensión de prueba de IU codificada para Excel](../test/sample-coded-ui-test-extension-for-excel.md)
