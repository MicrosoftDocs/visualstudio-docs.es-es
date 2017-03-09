---
title: "Complemento de Excel de muestra para probar la IU codificada | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pruebas de interfaz de usuario codificadas, Muestra de complemento de Excel"
ms.assetid: 2cd52d1a-4c35-43ca-8a84-9c79dabd907f
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "mlearned"
manager: "douge"
---
# Complemento de Excel de muestra para probar la IU codificada
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este complemento de ejemplo para [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] está diseñado específicamente para admitir las pruebas de interfaz de usuario codificadas de las hojas de cálculo de Excel que se registran y se ejecutan en Visual Studio Enterprise. El complemento se crea con Visual Studio Tools para Office.  
  
 Para obtener más información sobre cómo crear un complemento de Excel, vea [Tutorial: Crear el primer complemento de VSTO para Excel](../Topic/Walkthrough:%20Creating%20Your%20First%20VSTO%20Add-in%20for%20Excel.md) o busque "Excel Add\-In" en MSDN.  
  
 Aunque el complemento de Excel no es el tema principal de esta documentación de la extensión de prueba de IU codificada para Excel, algunos comentarios pueden resultar útiles.  
  
 Partes importantes de este complemento:  
  
-   Clase `ThisAddIn`: administra el canal de .NET Remoting entre `ExcelUICommunicator` y la [Extensión de muestra para probar la IU codificada para Excel](../test/sample-coded-ui-test-extension-for-excel.md).  
  
-   `ExcelCodedUIAddinHelper_TemporaryKey.pfx` : certificado de seguridad para probar el complemento.  
  
-   Clase `ExcelUICommunicator`: implementa la interfaz `IExcelUICommunication`.  
  
## Clase ThisAddIn  
 La mayor parte de esta clase se genera mediante Visual Studio Tools para Office en el archivo `ThisAddIn.Designer.cs` cuando se crea el proyecto de complemento de Excel.  
  
 Los miembros que debe implementar son los controladores de eventos `ThisAddIn_Startup()` y `ThisAddIn_Shutdown()`.  Su propósito es inicializar o cerrar el canal de .NET Remoting que `ExcelUICommunicator` usa.  
  
## ExcelCodedUIAddinHelper\_TemporaryKey.pfx  
 Este archivo contiene un certificado de seguridad temporal que se genera mediante Visual Studio Tools para Office y concede el permiso del ensamblado del complemento para que funcione en el proceso de Excel para probar el complemento y la extensión.  Debe eliminar este certificado y crear uno nuevo en la pestaña **Firma** de la ventana **Propiedades** del proyecto o bien adjuntar su propio certificado de pruebas.  
  
## Clase ExcelUICommunicator  
 Esta clase implementa la interfaz `IExcelUITestCommunication` y obtiene la información solicitada de la interfaz de usuario a partir del modelo de objetos de Excel.  Para obtener más información, consulte [Interfaz de muestra del Communicator de Excel](../test/sample-excel-communicator-interface.md).  
  
## Vea también  
 [Extender las pruebas de IU codificadas y las grabaciones de acciones para la compatibilidad con Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)   
 [Tutorial: Crear el primer complemento de VSTO para Excel](../Topic/Walkthrough:%20Creating%20Your%20First%20VSTO%20Add-in%20for%20Excel.md)   
 [Office and SharePoint Development](/office-dev/office-dev/office-and-sharepoint-development-in-visual-studio)