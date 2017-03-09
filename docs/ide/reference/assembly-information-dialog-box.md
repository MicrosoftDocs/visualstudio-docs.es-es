---
title: "Informaci&#243;n de ensamblado (Cuadro de di&#225;logo) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ProjectPropertiesAssemblyInfo"
helpviewer_keywords: 
  - "Cuadro de diálogo Información de ensamblado"
ms.assetid: 8f1f6449-e03d-4a5b-9076-d3b1f84ada48
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Informaci&#243;n de ensamblado (Cuadro de di&#225;logo)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

El cuadro de diálogo **Información de ensamblado** se utiliza para especificar los valores de los atributos de ensamblado globales de [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)], que se almacenan en el archivo AssemblyInfo creado automáticamente con el proyecto.  En el **Explorador de soluciones**, el archivo se encuentra en el nodo **Mi proyecto** de [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] \(haga clic en **Mostrar todos los archivos** para verlo\); se encuentra en la opción **Propiedades** de [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)].  Para obtener más información sobre los atributos de ensamblados, consulte [Atributos](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md).  
  
 Para tener acceso a este cuadro de diálogo, seleccione un nodo de proyecto en el **Explorador de soluciones** y, a continuación, en el menú **Proyecto** haga clic en **Propiedades**.  Cuando aparezca el **Diseñador de proyectos**, haga clic en la ficha **Aplicación**.  En la página **Aplicación**, haga clic en el botón **Información de ensamblado**.  
  
## Lista de UIElement  
 **Título**  
 Especifica un título para el manifiesto del ensamblado.  Corresponde a <xref:System.Reflection.AssemblyTitleAttribute>.  
  
 **Descripción**  
 Especifica una descripción opcional para el manifiesto del ensamblado.  Corresponde a <xref:System.Reflection.AssemblyDescriptionAttribute>.  
  
 **Compañía**  
 Especifica un nombre de compañía para el manifiesto del ensamblado.  Corresponde a <xref:System.Reflection.AssemblyCompanyAttribute>.  
  
 **Producto**  
 Especifica un nombre de producto para el manifiesto del ensamblado.  Corresponde a <xref:System.Reflection.AssemblyProductAttribute>.  
  
 **Copyright**  
 Especifica un aviso de copyright para el manifiesto del ensamblado.  Corresponde a <xref:System.Reflection.AssemblyCopyrightAttribute>.  
  
 **Marca comercial**  
 Especifica una marca comercial para el manifiesto del ensamblado.  Corresponde a <xref:System.Reflection.AssemblyTrademarkAttribute>.  
  
 **Versión de ensamblado**  
 Especifica la versión del ensamblado.  Corresponde a <xref:System.Reflection.AssemblyVersionAttribute>.  
  
 **Versión de archivo**  
 Especifica un número de versión que indica al compilador que debe utilizar una versión concreta para el recurso Win32 de versión de archivo.  Corresponde a <xref:System.Reflection.AssemblyFileVersionAttribute>.  
  
 **GUID**  
 Un GUID único que identifica el ensamblado.  Cuando crea un proyecto, Visual Studio genera un GUID para el ensamblado.  Corresponde a <xref:System.Guid>.  
  
 **Idioma neutro**  
 Especifica la referencia cultural admitida por el ensamblado.  Corresponde a <xref:System.Resources.NeutralResourcesLanguageAttribute>.  El valor predeterminado es **\(Ninguno\)**.  
  
 **Crear ensamblado visible a través de COM**  
 Especifica si COM podrá tener acceso a los tipos que se encuentran en el ensamblado.  Corresponde a <xref:System.Runtime.InteropServices.ComVisibleAttribute>.  
  
## Vea también  
 [Aplicación \(Página, Diseñador de proyectos\) \(Visual Basic\)](../../ide/reference/application-page-project-designer-visual-basic.md)   
 [Atributos](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)