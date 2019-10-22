---
title: Información de ensamblado (Cuadro de diálogo) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAssemblyInfo
helpviewer_keywords:
- Assembly Information dialog box
ms.assetid: 8f1f6449-e03d-4a5b-9076-d3b1f84ada48
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 06374f70c2552f3e635ada3bc40ef82d890fb46b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661024"
---
# <a name="assembly-information-dialog-box"></a>Información de ensamblado (Cuadro de diálogo)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

El cuadro de diálogo **Información de ensamblado** se usa para especificar los valores de los atributos de ensamblado globales de [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], que se almacenan en el archivo AssemblyInfo creado automáticamente con el proyecto. En el **Explorador de soluciones**, el archivo se encuentra en el nodo **Mi proyecto** en [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] (haga clic en **Mostrar todos los archivos** para verlo); se encuentra en **Propiedades** en [!INCLUDE[csprcs](../../includes/csprcs-md.md)]. Para obtener más información sobre atributos de ensamblado, consulte [Atributos](https://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205).

 Para acceder a este cuadro de diálogo, seleccione un nodo de proyecto en el **Explorador de soluciones** y después, en el menú **Proyecto**, haga clic en **Propiedades**. Cuando aparezca el **Diseñador de proyectos**, haga clic en la pestaña **Aplicación**. En la página **Aplicación**, haga clic en el botón **Información de ensamblado**.

## <a name="uielement-list"></a>Lista de UIElement
 **Título** Especifica un título para el manifiesto del ensamblado. Se corresponde con <xref:System.Reflection.AssemblyTitleAttribute>.

 **Descripción** Especifica una descripción opcional para el manifiesto del ensamblado. Se corresponde con <xref:System.Reflection.AssemblyDescriptionAttribute>.

 **Empresa** Especifica un nombre de empresa para el manifiesto del ensamblado. Se corresponde con <xref:System.Reflection.AssemblyCompanyAttribute>.

 **Producto** Especifica un nombre de producto para el manifiesto del ensamblado. Se corresponde con <xref:System.Reflection.AssemblyProductAttribute>.

 **Copyright** Especifica un aviso de copyright para el manifiesto del ensamblado. Se corresponde con <xref:System.Reflection.AssemblyCopyrightAttribute>.

 **Marca comercial** Especifica una marca comercial para el manifiesto del ensamblado. Se corresponde con <xref:System.Reflection.AssemblyTrademarkAttribute>.

 **Versión del ensamblado** Especifica la versión del ensamblado. Se corresponde con <xref:System.Reflection.AssemblyVersionAttribute>.

 **Versión del archivo** Especifica un número de versión que indica al compilador que use una versión determinada para el recurso de versión de archivo Win32. Se corresponde con <xref:System.Reflection.AssemblyFileVersionAttribute>.

 **GUID** Un GUID único que identifica el ensamblado. Al crear un proyecto, Visual Studio genera un GUID para el ensamblado. Se corresponde con <xref:System.Guid>.

 **Idioma neutro** Especifica la referencia cultural que admite el ensamblado. Se corresponde con <xref:System.Resources.NeutralResourcesLanguageAttribute>. El valor predeterminado es **(None)** .

 **Crear ensamblado visible a través de COM** Especifica si los tipos del ensamblado están disponibles para COM. Se corresponde con <xref:System.Runtime.InteropServices.ComVisibleAttribute>.

## <a name="see-also"></a>Otras referencias
 [Página de aplicación, atributos del diseñador de proyectos (Visual Basic)](../../ide/reference/application-page-project-designer-visual-basic.md) [](https://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)
