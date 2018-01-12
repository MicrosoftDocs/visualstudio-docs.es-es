---
title: "Cómo: configurar la información de configuración para una solución de Office | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], configuration files
- configuration files [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 6f604fa40a9816d5e46593bc50fcb91f82d13325
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-set-up-configuration-information-for-an-office-solution"></a>Cómo: Establecer la información de configuración para una solución de Office
  Puede utilizar archivos de configuración para configurar las opciones que son específicas de las soluciones de Office. Puede especificar valores como directiva de enlace de ensamblados, objetos de comunicación remota, depuración y la configuración de seguimiento.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-configuration-file-to-your-office-project"></a>Para agregar un archivo de configuración al proyecto de Office  
  
1.  En el menú **Proyecto** , haga clic en **Agregar nuevo elemento**.  
  
2.  En el **categorías** panel, haga clic en **General**.  
  
3.  En el **plantillas** panel, seleccione **archivo de configuración de aplicación**.  
  
4.  En el **nombre** , escriba el mismo nombre que el ensamblado, con la extensión .config. Por ejemplo, un archivo de configuración de un ensamblado de proyecto de Excel llamado ExcelWorkbook1.dll se denominará ExcelWorkbook1.dll.config.  
  
5.  Haga clic en **Agregar**.  
  
6.  Cree el archivo de configuración según el esquema de archivo de configuración de aplicación. Para obtener más información, consulte [esquema de archivo de configuración de .NET Framework](/dotnet/framework/configure-apps/file-schema/index).  
  
 No hay ninguna consideración especial para usar archivos de configuración con proyectos de Office.  
  
## <a name="see-also"></a>Vea también  
 [Esquema de archivos de configuración de .NET Framework](/dotnet/framework/configure-apps/file-schema/index)   
 [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)   
 [Implementación de una solución de Office](../vsto/deploying-an-office-solution.md)  
  
  