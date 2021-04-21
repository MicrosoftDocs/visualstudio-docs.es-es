---
title: Personalizar una cinta de opciones para InfoPath
description: Aprenda que al personalizar la cinta de opciones Microsoft Office InfoPath, debe tener en cuenta dónde aparecerá la cinta de opciones personalizada en la aplicación.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- InfoPath [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], InfoPath
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 5af7c4ed2f396c5a806cc42c49c8f4209b6b5c2c
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828142"
---
# <a name="customize-a-ribbon-for-infopath"></a>Personalizar una cinta de opciones para InfoPath
  Al personalizar la Cinta en Microsoft Office InfoPath, debe tener en cuenta dónde aparecerá la Cinta personalizada en la aplicación. [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)] puede mostrar la Cinta en los tres tipos de ventanas de la aplicación InfoPath indicados a continuación:

- Ventanas que muestran una plantilla de formulario que se abre en modo de diseño.

- Ventanas que muestran un formulario basado en una plantilla de formulario.

- La ventana Vista previa de impresión.

  **Aplicación:** la información de este tema se aplica a los proyectos de complemento VSTO para InfoPath 2010. Para obtener más información, vea [Características disponibles por aplicación de Office y tipo de proyecto](../vsto/features-available-by-office-application-and-project-type.md).

  Los usuarios y diseñadores abren una plantilla de formulario en modo de diseño para modificar la apariencia y el diseño de la plantilla. Los usuarios abren formularios basados en una plantilla de formulario para agregar contenido.

  La ventana Vista previa de impresión permite a los diseñadores y usuarios obtener una vista previa de las páginas de un formulario o de una plantilla de formulario antes de imprimirlas.

> [!NOTE]
> La pestaña **Complementos** no aparece en la ventana Vista previa de impresión. Si desea que una pestaña personalizada aparezca en la ventana Vista previa de impresión, asegúrese de que la propiedad **OfficeId** no se establezca en **TabAddIns**.

 Debe especificar el tipo de Cinta de cada ventana en la que desea que aparezca su Cinta.

## <a name="specify-the-ribbon-type-in-the-ribbon-designer"></a>Especificar el tipo de cinta de opciones en el diseñador de cintas
 Si usa el elemento **Cinta de opciones (Diseñador visual),** haga  clic en la propiedad **RibbonType** de la cinta de opciones en la ventana Propiedades y, a continuación, seleccione cualquiera de los IDs de la cinta que se describen en la tabla siguiente.

|Id. de Cinta|Ventana en la que aparecerá la Cinta al ejecutar el proyecto|
|---------------|---------------------------------------------------------------------|
|**Microsoft.InfoPath.Designer**|Ventanas que muestran una plantilla de formulario que se abre en modo de diseño.|
|**Microsoft.InfoPath.Editor**|Ventanas que muestran un formulario basado en una plantilla de formulario.|
|**Microsoft.InfoPath.PrintPreview**|La ventana Vista previa de impresión.|

 Puede agregar más de una Cinta a un proyecto. Si más de una Cinta comparte el mismo Id. de Cinta, reemplace el método `CreateRibbonExtensibilityObject` de la clase `ThisAddin` de su proyecto para especificar qué Cinta se mostrará en tiempo de ejecución. Para obtener más información, vea Información general [de la cinta de opciones.](../vsto/ribbon-overview.md)

## <a name="specify-the-ribbon-type-by-using-ribbon-xml"></a>Especificar el tipo de cinta de opciones mediante XML de cinta
 Si está utilizando el elemento **Cinta (XML)** , compruebe el valor del parámetro *ribbonID* en el método <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> y devuelva la Cinta adecuada.

 Visual Studio genera automáticamente el método <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> en el archivo de código de la Cinta. El parámetro *ribbonID* es una cadena que identifica el tipo de ventana de InfoPath que se está abriendo.

 En el siguiente ejemplo de código se indica cómo mostrar una Cinta personalizada sólo en una ventana que muestra una plantilla de formulario en modo de diseño. La Cinta que se debe mostrar se especifica en el método `GetResourceText()` , que se genera en la clase Cinta. Para obtener más información sobre la clase Cinta de opciones, consulte [Ribbon XML](../vsto/ribbon-xml.md).

 :::code language="csharp" source="../vsto/codesnippet/CSharp/myinfopathproject/ribbon.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/myinfopathproject/ribbon.vb" id="Snippet1":::

## <a name="see-also"></a>Consulte también
- [Acceso a la cinta de opciones en tiempo de ejecución](../vsto/accessing-the-ribbon-at-run-time.md)
- [Información general sobre la cinta de opciones](../vsto/ribbon-overview.md)
- [Diseñador de cinta de opciones](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
