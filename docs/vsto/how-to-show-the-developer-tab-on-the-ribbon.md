---
title: 'Cómo: mostrar la pestaña Programador en la cinta de opciones | Documentos de Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- Developer tab [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9921c10d8a886eb4051b3d5f3d8392ddc77c2da7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-show-the-developer-tab-on-the-ribbon"></a>Cómo: Mostrar la pestaña Programador en la cinta de opciones
  Para tener acceso a la **Developer** ficha en la cinta de opciones de una aplicación de Office, debe configurarlo para mostrar esa pestaña, ya que no aparece de forma predeterminada. Por ejemplo, debe mostrar esa pestaña si desea agregar un <xref:Microsoft.Office.Tools.Word.GroupContentControl> a una personalización de nivel de documento para Word.  
  
> [!NOTE]  
>  Esta guía se aplica únicamente a aplicaciones de Office 2010 o versiones posteriores. Si desea mostrar u ocultar esta ficha en 2007 Microsoft Office System, consulte la siguiente versión de este tema [Cómo: mostrar la pestaña Programador en la cinta de opciones](http://msdn.microsoft.com/library/bb608625(v=vs.90).aspx).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
> [!NOTE]  
>  No tiene acceso a un **Developer** ficha.  
  
### <a name="to-show-the-developer-tab"></a>Para mostrar la pestaña Desarrollador  
  
1.  Inicie cualquiera de las aplicaciones de Office compatibles con este tema. Consulte la **se aplica a:** Nota anteriormente en este tema.  
  
2.  En el **archivo** ficha, elija la **opciones** botón.  
  
     La siguiente ilustración muestra la **archivo** ficha y **opciones** botón de Office 2010.  
  
     ![Elegir archivos, opciones de Outlook 2010](../vsto/media/vsto-office-file-tab.png "elegir archivos, opciones de Outlook 2010")  
  
     La siguiente ilustración muestra la **archivo** ficha en Office 2013.  
  
     ![La pestaña del archivo de Outlook 2013](../vsto/media/vsto-office2013-filetab.png "pestaña del archivo de Outlook 2013")  
  
     La siguiente ilustración muestra la **opciones** botón en Office 2013.  
  
     ![El botón de opciones de Outlook 2013 Preview](../vsto/media/vsto-office2013-optionsbutton.png "el botón Opciones de Outlook 2013 Preview")  
  
3.  En el *ApplicationName *** opciones** diálogo cuadro, elija la **personalizar la cinta de opciones** botón.  
  
     La siguiente ilustración muestra la **opciones** cuadro de diálogo y el **personalizar la cinta de opciones** botón en Excel 2010. La ubicación de este botón es similar en el resto de las aplicaciones que se enumeran en la sección "Se aplica a" cerca de la parte superior de este tema.  
  
     ![El botón Personalizar la cinta de opciones](../vsto/media/vsto-office2010-customizeribbonbutton.png "botón de la cinta de opciones personalizar")  
  
4.  En la lista de pestañas principales, seleccione la **Developer** casilla de verificación.  
  
     La siguiente ilustración muestra la **Developer** casilla de verificación en Word 2010 y [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)]. La ubicación de esta casilla de verificación es similar en el resto de las aplicaciones que se enumeran en la sección "Se aplica a" cerca de la parte superior de este tema.  
  
     ![La casilla de verificación desarrollador en el cuadro de diálogo Opciones de Word](../vsto/media/vsto-office2010-developercheckbox.png "desarrollador la casilla de verificación en el cuadro de diálogo Opciones de Word")  
  
5.  Elija la **Aceptar** botón para cerrar la **opciones** cuadro de diálogo.  
  
## <a name="see-also"></a>Vea también  
 [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md)  
  
  