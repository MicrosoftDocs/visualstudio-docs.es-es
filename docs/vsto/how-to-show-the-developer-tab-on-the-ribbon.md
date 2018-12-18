---
title: 'Cómo: mostrar la pestaña Programador en la cinta de opciones'
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
ms.openlocfilehash: edcbcb969e45403d9ca138b259073e3cf4d73be0
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2018
ms.locfileid: "51349629"
---
# <a name="how-to-show-the-developer-tab-on-the-ribbon"></a>Cómo: mostrar la pestaña Programador en la cinta de opciones
  Para tener acceso a la **Developer** pestaña en la cinta de una aplicación de Office, debe configurarlo para mostrar esa pestaña, ya que no aparece de forma predeterminada. Por ejemplo, debe mostrar esa pestaña si desea agregar un <xref:Microsoft.Office.Tools.Word.GroupContentControl> a una personalización de nivel de documento para Word.  
  
> [!NOTE]  
>  Esta guía se aplica únicamente a aplicaciones de Office 2010 o versiones posteriores. Si desea mostrar esta pestaña en 2007 Microsoft Office System, vea la siguiente versión de este tema [Cómo: mostrar la pestaña Programador en la cinta de opciones](https://web.archive.org/web/20140303033431/msdn.microsoft.com/library/bb608625(v=vs.90).aspx
).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
> [!NOTE]  
>  No tiene acceso un **Developer** ficha.  
  
## <a name="to-show-the-developer-tab"></a>Para mostrar la pestaña Desarrollador  
  
1.  Inicie cualquiera de las aplicaciones de Office compatibles con este tema. Consulte la **se aplica a:** Nota anteriormente en este tema.  
  
2.  En el **archivo** ficha, elija la **opciones** botón.  
  
     La siguiente ilustración muestra el **archivo** pestaña y **opciones** botón de Office 2010.  
  
     ![Selección de archivo, opciones de Outlook 2010](../vsto/media/vsto-office-file-tab.png "Elegir archivo, opciones de Outlook 2010")  
  
     La siguiente ilustración muestra el **archivo** ficha en Office 2013.  
  
     ![La pestaña de archivo en Outlook 2013](../vsto/media/vsto-office2013-filetab.png "pestaña del archivo de Outlook 2013")  
  
     La siguiente ilustración muestra el **opciones** botón en Office 2013.  
  
     ![El botón Opciones en Outlook 2013 Preview](../vsto/media/vsto-office2013-optionsbutton.png "el botón Opciones en Outlook 2013 Preview")  
  
3.  En el _ApplicationName_**opciones** diálogo cuadro, elija el **personalizar la cinta de opciones** botón.  
  
     La siguiente ilustración muestra el **opciones** cuadro de diálogo y el **personalizar la cinta de opciones** botón en Excel 2010. La ubicación de este botón es similar en el resto de las aplicaciones que se enumeran en la sección "Se aplica a" cerca de la parte superior de este tema.  
  
     ![El botón Personalizar la cinta de opciones](../vsto/media/vsto-office2010-customizeribbonbutton.png "botón Personalizar la cinta")  
  
4.  En la lista de pestañas principales, seleccione el **Developer** casilla de verificación.  
  
     La siguiente ilustración muestra el **Developer** casilla de verificación en Word 2010 y [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)]. La ubicación de esta casilla de verificación es similar en el resto de las aplicaciones que se enumeran en la sección "Se aplica a" cerca de la parte superior de este tema.  
  
     ![La casilla de verificación desarrollador en el cuadro de diálogo Opciones de Word](../vsto/media/vsto-office2010-developercheckbox.png "para desarrolladores de la casilla de verificación en el cuadro de diálogo Opciones de Word")  
  
5.  Elija la **Aceptar** botón para cerrar el **opciones** cuadro de diálogo.  
  
## <a name="see-also"></a>Vea también  
 [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md)  
  
  