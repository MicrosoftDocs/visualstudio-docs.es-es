---
title: "Información de ensamblado (Cuadro de diálogo) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vb.ProjectPropertiesAssemblyInfo
helpviewer_keywords: Assembly Information dialog box
ms.assetid: 8f1f6449-e03d-4a5b-9076-d3b1f84ada48
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2bf115cdf81acbadab719eff5a19905c59832af8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="assembly-information-dialog-box"></a>Información de ensamblado (Cuadro de diálogo)
El cuadro de diálogo **Información de ensamblado** se usa para especificar los valores de los atributos de ensamblado globales de [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)], que se almacenan en el archivo AssemblyInfo creado automáticamente con el proyecto. En el **Explorador de soluciones**, el archivo se encuentra en el nodo **Mi proyecto** en [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] (haga clic en **Mostrar todos los archivos** para verlo); se encuentra en **Propiedades** en [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]. Para obtener más información sobre atributos de ensamblado, consulte [Atributos](http://msdn.microsoft.com/Library/ae334cee-d96c-4243-a5e3-06dd7fcaf205).  
  
 Para acceder a este cuadro de diálogo, seleccione un nodo de proyecto en el **Explorador de soluciones** y después, en el menú **Proyecto**, haga clic en **Propiedades**. Cuando aparezca el **Diseñador de proyectos**, haga clic en la pestaña **Aplicación**. En la página **Aplicación**, haga clic en el botón **Información de ensamblado**.  
  
## <a name="uielement-list"></a>Lista de UIElement  
 **Título**  
 Especifica un título para el manifiesto del ensamblado. Se corresponde con <xref:System.Reflection.AssemblyTitleAttribute>.  
  
 **Descripción**  
 Especifica una descripción opcional para el manifiesto del ensamblado. Se corresponde con <xref:System.Reflection.AssemblyDescriptionAttribute>.  
  
 **Empresa**  
 Especifica un nombre de empresa para el manifiesto del ensamblado. Se corresponde con <xref:System.Reflection.AssemblyCompanyAttribute>.  
  
 **Producto**  
 Especifica un nombre de producto para el manifiesto del ensamblado. Se corresponde con <xref:System.Reflection.AssemblyProductAttribute>.  
  
 **Copyright**  
 Especifica un aviso de copyright para el manifiesto del ensamblado. Se corresponde con <xref:System.Reflection.AssemblyCopyrightAttribute>.  
  
 **Marca comercial**  
 Especifica una marca comercial para el manifiesto del ensamblado. Se corresponde con <xref:System.Reflection.AssemblyTrademarkAttribute>.  
  
 **Versión de ensamblado**  
 Especifica la versión del ensamblado. Se corresponde con <xref:System.Reflection.AssemblyVersionAttribute>.  
  
 **Versión de archivo**  
 Especifica un número de versión que indica al compilador que use una versión específica para el recurso de versión de archivo Win32. Se corresponde con <xref:System.Reflection.AssemblyFileVersionAttribute>.  
  
 **GUID**  
 Un GUID único que identifica el ensamblado. Al crear un proyecto, Visual Studio genera un GUID para el ensamblado. Se corresponde con <xref:System.Guid>.  
  
 **Independiente del idioma**  
 Especifica la cultura que admite el ensamblado. Se corresponde con <xref:System.Resources.NeutralResourcesLanguageAttribute>. El valor predeterminado es **(None)**.  
  
 **Crear ensamblado visible a través de COM**  
 Especifica si los tipos del ensamblado estarán disponibles para COM. Se corresponde con <xref:System.Runtime.InteropServices.ComVisibleAttribute>.  
  
## <a name="see-also"></a>Vea también  
 [Página de aplicación, Diseñador de proyectos (Visual Basic)](../../ide/reference/application-page-project-designer-visual-basic.md)   
 [Atributos](http://msdn.microsoft.com/Library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)