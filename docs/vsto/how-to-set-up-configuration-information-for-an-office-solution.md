---
title: Configurar la información de configuración para una solución de Office
description: Obtenga información acerca de cómo puede usar los archivos de configuración para configurar opciones específicas para las soluciones de Microsoft Office.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], configuration files
- configuration files [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: da3a08ad9b3f6c78a10891e7d8ef2093ab46305d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927709"
---
# <a name="how-to-set-up-configuration-information-for-an-office-solution"></a>Cómo: configurar la información de configuración de una solución de Office
  Puede usar archivos de configuración para configurar opciones específicas para las soluciones de Office. Puede especificar valores como la Directiva de enlace de ensamblados, objetos de comunicación remota, depuración y configuración de seguimiento.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-a-configuration-file-to-your-office-project"></a>Para agregar un archivo de configuración a su proyecto de Office

1. En el menú **Proyecto** , haga clic en **Agregar nuevo elemento**.

2. En el panel **categorías** , haga clic en **General**.

3. En el panel **plantillas** , seleccione **archivo de configuración** de la aplicación.

4. En el cuadro **nombre** , escriba el mismo nombre que el ensamblado más el *archivo Extension. config*. Por ejemplo, un archivo de configuración para un ensamblado de proyecto de Excel denominado *ExcelWorkbook1.dll* se denominaría *ExcelWorkbook1.dll.config*.

5. Haga clic en **Agregar**.

6. Cree el archivo de configuración según el esquema del archivo de configuración de la aplicación. Para obtener más información, vea [esquema del archivo de configuración para el .NET Framework](/dotnet/framework/configure-apps/file-schema/index).

   No hay ninguna consideración especial para usar archivos de configuración con proyectos de Office.

## <a name="see-also"></a>Vea también
- [Esquema del archivo de configuración para el .NET Framework](/dotnet/framework/configure-apps/file-schema/index)
- [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)
- [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)
