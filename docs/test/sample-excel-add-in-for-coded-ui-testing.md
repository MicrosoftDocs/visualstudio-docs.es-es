---
title: Complemento de Excel de muestra para probar la IU codificada| Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- coded UI tests, Excel Add-in sample
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: d6033b10ec7b8be4e44ad00c6f550d7237806234
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/09/2018
---
# <a name="sample-excel-add-in-for-coded-ui-testing"></a>Complemento de Excel de muestra para probar la IU codificada
Este complemento de ejemplo para [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] está diseñado específicamente para admitir las pruebas de interfaz de usuario codificadas de las hojas de cálculo de Excel que se registran y se ejecutan en Visual Studio Enterprise. El complemento se crea con Visual Studio Tools para Office.  
  
 Para obtener más información sobre cómo crear un complemento de Excel, vea [Tutorial: Crear el primer complemento de VSTO para Excel](http://msdn.microsoft.com/Library/a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f) o busque "Complemento Excel" en MSDN.  
  
 Aunque el complemento de Excel no es el tema principal de esta documentación de la extensión de prueba de IU codificada para Excel, algunos comentarios pueden resultar útiles.  
  
 Partes importantes de este complemento:  
  
-   Clase `ThisAddIn`: administra el canal de .NET Remoting entre `ExcelUICommunicator` y la [Extensión de muestra para probar la interfaz de usuario codificada para Excel](../test/sample-coded-ui-test-extension-for-excel.md).  
  
-   `ExcelCodedUIAddinHelper_TemporaryKey.pfx`: certificado de seguridad para probar el complemento.  
  
-   Clase `ExcelUICommunicator`: implementa la interfaz `IExcelUICommunication`.  
  
## <a name="thisaddin-class"></a>Clase ThisAddIn  
 La mayor parte de esta clase se genera mediante Visual Studio Tools para Office en el archivo `ThisAddIn.Designer.cs` cuando se crea el proyecto de complemento de Excel.  
  
 Los miembros que debe implementar son los controladores de eventos `ThisAddIn_Startup()` y `ThisAddIn_Shutdown()`. Su propósito es inicializar o cerrar el canal de .NET Remoting que `ExcelUICommunicator` usa.  
  
## <a name="excelcodeduiaddinhelpertemporarykeypfx"></a>ExcelCodedUIAddinHelper_TemporaryKey.pfx  
 Este archivo contiene un certificado de seguridad temporal que se genera mediante Visual Studio Tools para Office y concede el permiso del ensamblado del complemento para que funcione en el proceso de Excel para probar el complemento y la extensión. Debe eliminar este certificado y crear uno nuevo en la pestaña **Firma** de la ventana **Propiedades** del proyecto o bien adjuntar su propio certificado de pruebas.  
  
## <a name="exceluicommunicator-class"></a>Clase ExcelUICommunicator  
 Esta clase implementa la interfaz `IExcelUITestCommunication` y obtiene la información solicitada de la interfaz de usuario a partir del modelo de objetos de Excel. Para obtener más información, consulte [Interfaz de muestra del Communicator de Excel](../test/sample-excel-communicator-interface.md).  
  
## <a name="see-also"></a>Vea también  
 [Extender las pruebas de IU codificadas y las grabaciones de acciones para la compatibilidad con Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)   
 [Tutorial: Crear el primer complemento de VSTO para Excel](http://msdn.microsoft.com/Library/a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f)   
 [Desarrollo de Office y SharePoint](/office-dev/office-dev/office-and-sharepoint-development-in-visual-studio)
