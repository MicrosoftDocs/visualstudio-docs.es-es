---
title: "Personalizar una Cinta para InfoPath"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "InfoPath [desarrollo de Office en Visual Studio], Cinta de opciones"
  - "Cinta de opciones [desarrollo de Office en Visual Studio], InfoPath"
ms.assetid: 498c6457-679a-46f2-939f-c0597a17b7ec
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# Personalizar una Cinta para InfoPath
  Al personalizar la Cinta en Microsoft Office InfoPath, debe tener en cuenta dónde aparecerá la Cinta personalizada en la aplicación.[!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)] puede mostrar la Cinta en los tres tipos de ventanas de la aplicación InfoPath indicados a continuación:  
  
-   Ventanas que muestran una plantilla de formulario que se abre en modo de diseño.  
  
-   Ventanas que muestran un formulario basado en una plantilla de formulario.  
  
-   La ventana Vista previa de impresión.  
  
 **Aplicación:** la información de este tema se aplica a los proyectos de complemento VSTO para InfoPath 2010. Para obtener más información, consulta [Características disponibles por aplicación y tipo de proyecto de Office](../vsto/features-available-by-office-application-and-project-type.md).  
  
 Los usuarios y diseñadores abren una plantilla de formulario en modo de diseño para modificar la apariencia y el diseño de la plantilla. Los usuarios abren formularios basados en una plantilla de formulario para agregar contenido.  
  
 La ventana Vista previa de impresión permite a los diseñadores y usuarios obtener una vista previa de las páginas de un formulario o de una plantilla de formulario antes de imprimirlas.  
  
> [!NOTE]  
>  La pestaña **Complementos** no aparece en la ventana Vista previa de impresión. Si desea que una pestaña personalizada aparezca en la ventana Vista previa de impresión, asegúrese de que la propiedad **OfficeId** no se establezca en **TabAddIns**.  
  
 Debe especificar el tipo de Cinta de cada ventana en la que desea que aparezca su Cinta.  
  
## Especificar el Tipo de Cinta en el Diseñador de cinta  
 Si está utilizando el elemento **Cinta \(diseñador visual\)**, haga clic en la propiedad **RibbonType** de la cinta en la ventana **Propiedades** y, a continuación, seleccione cualquiera de los identificadores de cinta descritos en la siguiente tabla.  
  
|Id. de Cinta|Ventana en la que aparecerá la Cinta al ejecutar el proyecto|  
|------------------|------------------------------------------------------------------|  
|**Microsoft.InfoPath.Designer**|Ventanas que muestran una plantilla de formulario que se abre en modo de diseño.|  
|**Microsoft.InfoPath.Editor**|Ventanas que muestran un formulario basado en una plantilla de formulario.|  
|**Microsoft.InfoPath.PrintPreview**|La ventana Vista previa de impresión.|  
  
 Puede agregar más de una Cinta a un proyecto. Si más de una Cinta comparte el mismo Id. de Cinta, reemplace el método CreateRibbonExtensibilityObject de la clase `ThisAddin` de su proyecto para especificar qué Cinta se mostrará en tiempo de ejecución. Para obtener más información, consulta [Información general sobre la cinta de opciones](../vsto/ribbon-overview.md).  
  
## Especificar el Tipo de Cinta mediante código XML de Cinta  
 Si está utilizando el elemento **Cinta \(XML\)**, compruebe el valor del parámetro *ribbonID* en el método <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> y devuelva la Cinta adecuada.  
  
 Visual Studio genera automáticamente el método <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> en el archivo de código de la Cinta. El parámetro *ribbonID* es una cadena que identifica el tipo de ventana de InfoPath que se está abriendo.  
  
 En el siguiente ejemplo de código se indica cómo mostrar una Cinta personalizada sólo en una ventana que muestra una plantilla de formulario en modo de diseño. La Cinta que se debe mostrar se especifica en el método `GetResourceText()`, que se genera en la clase Cinta. Para obtener más información sobre la clase Cinta de opciones, consulte [XML de la cinta de opciones](../vsto/ribbon-xml.md).  
  
 [!code-csharp[Trin_RibbonInfoPathBasic#1](../snippets/csharp/VS_Snippets_OfficeSP/trin_ribboninfopathbasic/cs/ribbon.cs#1)]
 [!code-vb[Trin_RibbonInfoPathBasic#1](../snippets/visualbasic/VS_Snippets_OfficeSP/trin_ribboninfopathbasic/vb/ribbon.vb#1)]  
  
## Vea también  
 [Obtener acceso a la cinta de opciones en tiempo de ejecución](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Información general sobre la cinta de opciones](../vsto/ribbon-overview.md)   
 [Diseñador de la cinta de opciones](../vsto/ribbon-designer.md)   
 [XML de la cinta de opciones](../vsto/ribbon-xml.md)  
  
  