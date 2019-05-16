---
title: Complemento de Excel de muestra para probar la IU codificada| Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, Excel Add-in sample
ms.assetid: 2cd52d1a-4c35-43ca-8a84-9c79dabd907f
caps.latest.revision: 18
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8588efe9ce460a34fc71f44bc0116b5977afe7aa
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65705940"
---
# <a name="sample-excel-add-in-for-coded-ui-testing"></a>Complemento de Excel de muestra para probar la IU codificada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este complemento de ejemplo para [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] está diseñado específicamente para admitir las pruebas de interfaz de usuario codificadas de las hojas de cálculo de Excel que se registran y se ejecutan en Visual Studio Enterprise. El complemento se crea con Visual Studio Tools para Office.  
  
 Para obtener más información sobre cómo crear un complemento de Excel, vea [Tutorial: Crear el primer complemento de VSTO para Excel](https://msdn.microsoft.com/library/a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f) o busque en MSDN para "Excel Add-In".  
  
 Aunque el complemento de Excel no es el tema principal de esta documentación de la extensión de prueba de IU codificada para Excel, algunos comentarios pueden resultar útiles.  
  
 Partes importantes de este complemento:  
  
- Clase `ThisAddIn`: administra el canal de .NET Remoting entre `ExcelUICommunicator` y la [Extensión de muestra para probar la interfaz de usuario codificada para Excel](../test/sample-coded-ui-test-extension-for-excel.md).  
  
- `ExcelCodedUIAddinHelper_TemporaryKey.pfx`: certificado de seguridad para probar el complemento.  
  
- Clase `ExcelUICommunicator`: implementa la interfaz `IExcelUICommunication`.  
  
## <a name="thisaddin-class"></a>Clase ThisAddIn  
 La mayor parte de esta clase se genera mediante Visual Studio Tools para Office en el archivo `ThisAddIn.Designer.cs` cuando se crea el proyecto de complemento de Excel.  
  
 Los miembros que debe implementar son los controladores de eventos `ThisAddIn_Startup()` y `ThisAddIn_Shutdown()`. Su propósito es inicializar o cerrar el canal de .NET Remoting que `ExcelUICommunicator` usa.  
  
## <a name="excelcodeduiaddinhelpertemporarykeypfx"></a>ExcelCodedUIAddinHelper_TemporaryKey.pfx  
 Este archivo contiene un certificado de seguridad temporal que se genera mediante Visual Studio Tools para Office y concede el permiso del ensamblado del complemento para que funcione en el proceso de Excel para probar el complemento y la extensión. Debe eliminar este certificado y crear uno nuevo en la pestaña **Firma** de la ventana **Propiedades** del proyecto o bien adjuntar su propio certificado de pruebas.  
  
## <a name="exceluicommunicator-class"></a>Clase ExcelUICommunicator  
 Esta clase implementa la interfaz `IExcelUITestCommunication` y obtiene la información solicitada de la interfaz de usuario a partir del modelo de objetos de Excel. Para obtener más información, consulte [Interfaz de muestra del Communicator de Excel](../test/sample-excel-communicator-interface.md).  
  
## <a name="see-also"></a>Vea también  
 [Extender las pruebas de IU codificadas y las grabaciones de acciones para la compatibilidad con Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)   
 [Tutorial: Crear el primer complemento VSTO para Excel](https://msdn.microsoft.com/library/a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f)   
 [Desarrollo de Office y SharePoint](https://msdn.microsoft.com/library/2ddec047-263a-4901-a54c-a15fc8472329)
