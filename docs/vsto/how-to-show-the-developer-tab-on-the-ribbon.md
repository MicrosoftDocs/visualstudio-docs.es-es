---
title: 'Cómo: Mostrar la pestaña programador en la cinta de opciones'
description: Obtenga información sobre cómo puede usar Visual Studio para mostrar mediante programación la pestaña Desarrollador en la cinta de opciones en un documento de Microsoft Word.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- Developer tab [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 081d6740aa31a31173b12e467b1b8e32a074604a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927722"
---
# <a name="how-to-show-the-developer-tab-on-the-ribbon"></a>Cómo: Mostrar la pestaña programador en la cinta de opciones
  Para tener acceso a la pestaña **desarrollador** de la cinta de opciones de una aplicación de Office, debe configurarla para mostrar esa pestaña, ya que no aparece de forma predeterminada. Por ejemplo, debe mostrar esa pestaña si desea agregar un <xref:Microsoft.Office.Tools.Word.GroupContentControl> a una personalización de nivel de documento para Word.

> [!NOTE]
> Esta guía se aplica únicamente a aplicaciones de Office 2010 o versiones posteriores. Si desea mostrar esta pestaña en el sistema Microsoft Office 2007, vea la siguiente versión de este tema [Cómo: Mostrar la pestaña programador en la cinta de](https://web.archive.org/web/20140303033431/msdn.microsoft.com/library/bb608625(v=vs.90).aspx
)opciones.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

> [!NOTE]
> El acceso no tiene una pestaña **desarrollador** .

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="to-show-the-developer-tab"></a>Para mostrar la pestaña Desarrollador

1. Inicie cualquiera de las aplicaciones de Office compatibles con este tema. Vea la nota **se aplica a:** anteriormente en este tema.

2. En la pestaña **archivo** , elija el botón **Opciones** .

     En la siguiente ilustración se muestra la pestaña **archivo** y el botón **opciones** en Office 2010.

     ![Elegir Archivo, Opciones en Outlook 2010](../vsto/media/vsto-office-file-tab.png "Elegir Archivo, Opciones en Outlook 2010")

     En la siguiente ilustración se muestra la pestaña **archivo** de Office 2013.

     ![La pestaña Archivo de Outlook 2013](../vsto/media/vsto-office2013-filetab.png "La pestaña Archivo de Outlook 2013")

     En la siguiente ilustración se muestra el botón **Opciones** de Office 2013.

     ![El botón Opciones de Outlook 2013 Preview](../vsto/media/vsto-office2013-optionsbutton.png "El botón Opciones de Outlook 2013 Preview")

3. En el cuadro de diálogo Opciones de _applicationName_, elija el botón **personalizar la cinta** de **Opciones** .

     La siguiente ilustración muestra el cuadro de diálogo Opciones y el botón **personalizar la cinta** de **opciones** en Excel 2010. La ubicación de este botón es similar en el resto de las aplicaciones que se enumeran en la sección "Se aplica a" cerca de la parte superior de este tema.

     ![El botón Personalizar la cinta de opciones](../vsto/media/vsto-office2010-customizeribbonbutton.png "El botón Personalizar la cinta de opciones")

4. En la lista de pestañas principales, active la casilla **desarrollador** .

     En la siguiente ilustración se muestra la casilla **programador** en Word 2010 y [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] . La ubicación de esta casilla de verificación es similar en el resto de las aplicaciones que se enumeran en la sección "Se aplica a" cerca de la parte superior de este tema.

     ![La casilla Desarrollador del cuadro de diálogo Opciones de Word](../vsto/media/vsto-office2010-developercheckbox.png "La casilla Desarrollador del cuadro de diálogo Opciones de Word")

5. Elija el botón **Aceptar** para cerrar el cuadro de diálogo **Opciones** .

## <a name="see-also"></a>Vea también
- [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md)
