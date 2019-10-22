---
title: Personalizar el modo en que Visual Studio 2015 crea títulos para los controles enlazados a datos | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- Label captions, Data Sources window
- smart captions
- captions, data-bound
- Data Sources Window, label captions
ms.assetid: 6d4d15f8-4d78-42fd-af64-779ae98d62c8
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 04f32fa0426039f50c0a0352ef0b04900d705a98
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657440"
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>Personalizar el modo en que Visual Studio crea los títulos de controles enlazados a datos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Al arrastrar elementos desde la [ventana orígenes de datos](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) hasta el diseñador de Windows Forms, se produce una consideración especial: los nombres de columna de las etiquetas de título se vuelven a formatear en una cadena más legible cuando se encuentran concatenadas dos o más palabras. forma. Puede personalizar la forma en que se crean estas etiquetas estableciendo los valores **SmartCaptionExpression**, **SmartCaptionReplacement**y **SmartCaptionSuffix** en **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\ 10.0 \** clave del registro de los diseñadores de datos.

> [!NOTE]
> Esta clave del registro no existe hasta que se crea.

 Los subtítulos inteligentes se controlan mediante la expresión regular especificada en el valor de **SmartCaptionExpression** . Al agregar la clave del registro de los **diseñadores de datos** se invalida la expresión regular predeterminada que controla las etiquetas de título. Para obtener más información sobre las expresiones regulares, vea [usar expresiones regulares en Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

 En la tabla siguiente se describen los valores del registro que controlan las etiquetas de título.

|Elemento del registro|Descripción|
|-------------------|-----------------|
|**SmartCaptionExpression**|Expresión regular que se usa para hacer coincidir los patrones.|
|**SmartCaptionReplacement**|Formato en el que se van a mostrar los grupos coincidentes en **SmartCaptionExpression**.|
|**SmartCaptionSuffix**|Cadena opcional que se va a anexar al final del título.|

 En la tabla siguiente se muestra la configuración predeterminada interna de estos valores del registro.

|Elemento del registro|Valor predeterminado|Explicación|
|-------------------|-------------------|-----------------|
|**SmartCaptionExpression**|(\\ \p{Ll}) (\\ \p{Lu}) &#124;_+|Coincide con un carácter en minúscula seguido de un carácter en mayúsculas o un carácter de subrayado.|
|**SmartCaptionReplacement**|$1 $2|$1 representa los caracteres coincidentes en los primeros paréntesis de la expresión y el $2 representa los caracteres coincidentes en el segundo paréntesis. El reemplazo es la primera coincidencia, un espacio y, a continuación, la segunda coincidencia.|
|**SmartCaptionSuffix**|:|Representa un carácter anexado a la cadena devuelta. Por ejemplo, si el título es `Company Name`, el sufijo lo hace `Company Name:`|

> [!CAUTION]
> Debe tener mucho cuidado al realizar cualquier acción en el editor del registro. Realice una copia de seguridad del registro antes de editarlo. Si utiliza incorrectamente el editor del registro, puede ocasionar problemas graves que pueden requerir la reinstalación del sistema operativo. Microsoft no garantiza que se puedan resolver los problemas que se produzcan con el editor del registro de forma incorrecta. Utilice el editor del registro bajo su responsabilidad.
>
> El siguiente artículo de KnowledgeBase contiene instrucciones para realizar copias de seguridad, editar y restaurar el registro: [Descripción del registro de Microsoft Windows](http://support.microsoft.com/default.aspx?scid=kb;en-us;256986) (http://support.microsoft.com/default.aspx?scid=kb; en-US; 256986)

### <a name="to-modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>Para modificar el comportamiento de los subtítulos inteligentes de la ventana orígenes de datos

1. Abra una ventana de comandos haciendo clic en **Inicio** y, a continuación, en **Ejecutar**.

2. Escriba `regedit` en el cuadro de diálogo **Ejecutar** y haga clic en **Aceptar**.

3. Expanda el nodo **HKEY_CURRENT_USER** .

4. Expanda el nodo **software** .

5. Expanda el nodo **Microsoft** .

6. Expanda el nodo de **VisualStudio** .

7. Haga clic con el botón secundario en el nodo **10,0** y cree una nueva **clave** denominada `Data Designers`.

8. Haga clic con el botón secundario en el nodo **diseñadores de datos** y cree un nuevo **valor de cadena** denominado `SmartCaptionExpression`.

9. Haga clic con el botón secundario en el nodo **diseñadores de datos** y cree un nuevo **valor de cadena** denominado `SmartCaptionReplacement`.

10. Haga clic con el botón secundario en el nodo **diseñadores de datos** y cree un nuevo **valor de cadena** denominado `SmartCaptionSuffix`.

11. Haga clic con el botón secundario en el elemento **SmartCaptionExpression** y seleccione **modificar**.

12. Escriba la expresión regular que desea que use la ventana **orígenes de datos** .

13. Haga clic con el botón secundario en el elemento **SmartCaptionReplacement** y seleccione **modificar**.

14. Escriba la cadena de reemplazo con el formato que desea para mostrar los patrones coincidentes en la expresión regular.

15. Haga clic con el botón secundario en el elemento **SmartCaptionSuffix** y seleccione **modificar**.

16. Escriba los caracteres que desee que aparezcan al final del título.

     La próxima vez que arrastre elementos desde la ventana **orígenes de datos** , las etiquetas de título se crearán con los nuevos valores del registro proporcionados.

### <a name="to-turn-off-the-smart-captioning-feature"></a>Para desactivar la característica de subtítulos inteligentes

1. Abra una ventana de comandos haciendo clic en **Inicio** y, a continuación, en **Ejecutar**.

2. Escriba `regedit` en el cuadro de diálogo **Ejecutar** y haga clic en **Aceptar**.

3. Expanda el nodo **HKEY_CURRENT_USER** .

4. Expanda el nodo **software** .

5. Expanda el nodo **Microsoft** .

6. Expanda el nodo de **VisualStudio** .

7. Haga clic con el botón secundario en el nodo **10,0** y cree una nueva **clave** denominada `Data Designers`.

8. Haga clic con el botón secundario en el nodo **diseñadores de datos** y cree un nuevo **valor de cadena** denominado `SmartCaptionExpression`.

9. Haga clic con el botón secundario en el nodo **diseñadores de datos** y cree un nuevo **valor de cadena** denominado `SmartCaptionReplacement`.

10. Haga clic con el botón secundario en el nodo **diseñadores de datos** y cree un nuevo **valor de cadena** denominado `SmartCaptionSuffix`.

11. Haga clic con el botón secundario en el elemento **SmartCaptionExpression** y seleccione **modificar**.

12. Escriba `(.*)` para el valor. Coincide con toda la cadena.

13. Haga clic con el botón secundario en el elemento **SmartCaptionReplacement** y seleccione **modificar**.

14. Escriba `$1` para el valor. Esto reemplaza la cadena con el valor coincidente, que es toda la cadena para que permanezca sin cambios.

     La próxima vez que arrastre elementos desde la ventana **orígenes de datos** , las etiquetas de título se crearán con títulos sin modificar.

## <a name="see-also"></a>Vea también
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
