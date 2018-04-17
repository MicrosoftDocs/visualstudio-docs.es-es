---
title: 'Cómo: configurar la información de configuración para una solución de Office | Documentos de Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], configuration files
- configuration files [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9659872fa6cb4e294d1757412862c10e42cde2e9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
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
  
  