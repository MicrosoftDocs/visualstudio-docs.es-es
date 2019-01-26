---
title: Procedimiento Configurar la información de configuración para una solución de Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], configuration files
- configuration files [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9db171b038178c9fe0bd4ffc4fbb98b221b9b4d5
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54864480"
---
# <a name="how-to-set-up-configuration-information-for-an-office-solution"></a>Procedimiento Configurar la información de configuración para una solución de Office
  Puede usar los archivos de configuración para configurar las opciones que son específicas de las soluciones de Office. Puede especificar la configuración de directiva de enlace de ensamblados, objetos de comunicación remota, depuración y la configuración de seguimiento.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-configuration-file-to-your-office-project"></a>Para agregar un archivo de configuración al proyecto de Office  
  
1. En el menú **Proyecto** , haga clic en **Agregar nuevo elemento**.  
  
2. En el **categorías** panel, haga clic en **General**.  
  
3. En el **plantillas** panel, seleccione **archivo de configuración de aplicación**.  
  
4. En el **nombre** , escriba el mismo nombre que el ensamblado más la extensión *.config*. Por ejemplo, un archivo de configuración para un ensamblado de proyecto de Excel denominado *ExcelWorkbook1.dll* se denominará *ExcelWorkbook1.dll.config*.  
  
5. Haga clic en **Agregar**.  
  
6. Cree el archivo de configuración según el esquema de archivo de configuración de aplicación. Para obtener más información, consulte [esquema de archivo de configuración de .NET Framework](/dotnet/framework/configure-apps/file-schema/index).  
  
   No hay ninguna consideración especial para usar archivos de configuración con los proyectos de Office.  
  
## <a name="see-also"></a>Vea también  
 [Esquema de archivo de configuración de .NET Framework](/dotnet/framework/configure-apps/file-schema/index)   
 [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)   
 [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)  
