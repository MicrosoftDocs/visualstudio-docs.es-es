---
title: Procedimiento Mostrar la pestaña programador en la cinta de opciones
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- Developer tab [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7b6641cca4ef2288452b2f6959482b311a5b07a4
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551777"
---
# <a name="how-to-show-the-developer-tab-on-the-ribbon"></a>Procedimiento Mostrar la pestaña programador en la cinta de opciones
  Para tener acceso a la pestaña **desarrollador** de la cinta de opciones de una aplicación de Office, debe configurarla para mostrar esa pestaña, ya que no aparece de forma predeterminada. Por ejemplo, debe mostrar esa pestaña si desea agregar un <xref:Microsoft.Office.Tools.Word.GroupContentControl> a una personalización de nivel de documento para Word.

> [!NOTE]
> Esta guía se aplica únicamente a aplicaciones de Office 2010 o versiones posteriores. Si desea mostrar esta pestaña en el sistema Microsoft Office 2007, consulte la siguiente versión de este tema [: Mostrar la pestaña programador en la cinta](https://web.archive.org/web/20140303033431/msdn.microsoft.com/library/bb608625(v=vs.90).aspx
)de opciones.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

> [!NOTE]
> El acceso no tiene una pestaña **desarrollador** .

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="to-show-the-developer-tab"></a>Para mostrar la pestaña Desarrollador

1. Inicie cualquiera de las aplicaciones de Office compatibles con este tema. Vea la nota **se aplica a:** anteriormente en este tema.

2. En la pestaña **archivo** , elija el botón **Opciones** .

     En la siguiente ilustración se muestra la pestaña **archivo** y el botón **opciones** en Office 2010.

     ![Elegir archivo, opciones en Outlook 2010](../vsto/media/vsto-office-file-tab.png "Elegir archivo, opciones en Outlook 2010")

     En la siguiente ilustración se muestra la pestaña **archivo** de Office 2013.

     ![Pestaña archivo en Outlook 2013](../vsto/media/vsto-office2013-filetab.png "Pestaña archivo en Outlook 2013")

     En la siguiente ilustración se muestra el botón **Opciones** de Office 2013.

     ![Botón Opciones de Outlook 2013 Preview](../vsto/media/vsto-office2013-optionsbutton.png "Botón Opciones de Outlook 2013 Preview")

3. En el cuadro de diálogo Opciones de _applicationName_, elija el botón **personalizar la cinta** de**Opciones** .

     La siguiente ilustración muestra el cuadro de diálogo Opciones y el botón **personalizar la cinta** de **opciones** en Excel 2010. La ubicación de este botón es similar en el resto de las aplicaciones que se enumeran en la sección "Se aplica a" cerca de la parte superior de este tema.

     ![Botón personalizar la cinta de] opciones (../vsto/media/vsto-office2010-customizeribbonbutton.png "Botón personalizar la cinta de") opciones

4. En la lista de pestañas principales, active la casilla **desarrollador** .

     En la siguiente ilustración se muestra la casilla **programador** en Word 2010 [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)]y. La ubicación de esta casilla de verificación es similar en el resto de las aplicaciones que se enumeran en la sección "Se aplica a" cerca de la parte superior de este tema.

     ![Casilla Desarrollador en el cuadro de diálogo Opciones de Word](../vsto/media/vsto-office2010-developercheckbox.png "Casilla Desarrollador en el cuadro de diálogo Opciones de Word")

5. Elija el botón **Aceptar** para cerrar el cuadro de diálogo **Opciones** .

## <a name="see-also"></a>Vea también
- [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md)
