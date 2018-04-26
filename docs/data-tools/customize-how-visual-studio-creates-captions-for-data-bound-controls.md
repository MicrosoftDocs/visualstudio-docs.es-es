---
title: Personalizar el modo en que Visual Studio crea los títulos para los controles enlazados a datos
ms.date: 11/03/2017
ms.topic: conceptual
helpviewer_keywords:
- Label captions, Data Sources window
- smart captions
- captions, data-bound
- Data Sources Window, label captions
ms.assetid: 6d4d15f8-4d78-42fd-af64-779ae98d62c8
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: f6c2dffe793928532d36b539ba73914ecf0c24dc
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>Personalizar el modo en que Visual Studio crea los títulos para los controles enlazados a datos
Cuando se arrastran elementos desde la [ventana Orígenes de datos](add-new-data-sources.md) en un diseñador, entra en juego la cuenta una consideración especial: los nombres de columna en las etiquetas de leyenda se vuelve a dar formato a una cadena más legible cuando dos o más palabras se encuentran como se concatenan juntos. Puede personalizar la manera en que se crean estas etiquetas, estableciendo el **SmartCaptionExpression**, **SmartCaptionReplacement**, y **SmartCaptionSuffix** valores en el **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Data diseñadores** clave del registro.

> [!NOTE]
> Esta clave del registro no existe hasta que la cree.

Etiquetas inteligentes se controla mediante la expresión regular especificada en el valor de la **SmartCaptionExpression** valor. Agregar el **diseñadores datos** clave del registro invalida la expresión regular predeterminada que controla las etiquetas de título. Para obtener más información sobre las expresiones regulares, vea [usar expresiones regulares en Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

La tabla siguiente describen los valores del registro que controlan las etiquetas de título.

|Elemento del registro|Descripción|
|-------------------|-----------------|
|**SmartCaptionExpression**|La expresión regular utilizada para hacer coincidir los modelos.|
|**SmartCaptionReplacement**|El formato para mostrar los grupos que coinciden en el **SmartCaptionExpression**.|
|**SmartCaptionSuffix**|Una cadena opcional para anexar al final del título.|

En la tabla siguiente se muestra la configuración predeterminada interna para estos valores del registro.

|Elemento del registro|Valor predeterminado|Explicación|
|-------------------|-------------------|-----------------|
|**SmartCaptionExpression**|(\\\p{Ll}) (\\\p{Lu})&#124;_ +|Coincide con un carácter en minúscula seguido por un carácter en mayúscula o un carácter de subrayado.|
|**SmartCaptionReplacement**|$1 $2|$1 representa cualquier carácter coincidente en el primer paréntesis de la expresión y $2 representa cualquier carácter coincidente en la segundos paréntesis. La sustitución es la primera coincidencia, un espacio y, a continuación, en la segunda coincidencia.|
|**SmartCaptionSuffix**|:|Representa un carácter que se anexa a la cadena devuelta. Por ejemplo, si el título es `Company Name`, el sufijo facilita `Company Name:`|

> [!CAUTION]
> Debe tener mucho cuidado al hacer nada en el Editor del registro. Hacer copia de seguridad del registro antes de editarlo. Si utiliza incorrectamente el Editor del registro, puede provocar problemas graves que quizás requieran reinstalar el sistema operativo. Microsoft no garantiza que se pueden resolver los problemas que causan utilizando el Editor del Registro incorrectamente. Utilice el Editor del registro bajo su responsabilidad.
>
>  El siguiente artículo de Knowledge Base contiene instrucciones para realizar copias de seguridad, modificar y restaurar el registro: [descripción del registro de Microsoft Windows](http://support.microsoft.com/default.aspx?scid=kb;en-us;256986) (http://support.microsoft.com/default.aspx?scid=kb; en-us; 256986)

### <a name="to-modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>Para modificar el comportamiento de subtítulos (CC) inteligente de la ventana de orígenes de datos

1.  Abra una ventana de comandos, haga clic en **iniciar** y, a continuación, **ejecutar**.

2.  Tipo de `regedit` en el **ejecutar** cuadro de diálogo y haga clic en **Aceptar**.

3.  Expanda el **HKEY_CURRENT_USER**, **Software*, **Microsoft**, **VisualStudio** nodo.

7.  Haga clic en el **15.0** nodo y crear un nuevo **clave** denominado `Data Designers`.

8.  Haga clic en el **diseñadores datos** nodo y crear tres nuevos valores de cadena:

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`

11. Haga clic en el **SmartCaptionExpression** valor y seleccione **modificar**.

12. Escriba la expresión regular que desee la **orígenes de datos** ventana que usará.

13. Haga clic en el **SmartCaptionReplacement** valor y seleccione **modificar**.

14. Escriba el reemplazo de cadena de formato que desea mostrar los modelos que coinciden en la expresión regular.

15. Haga clic en el **SmartCaptionSuffix** valor y seleccione **modificar**.

16. Escriba los caracteres que desea que aparezcan al final del título.

    La próxima vez que se arrastran elementos desde la **orígenes de datos** ventana, las etiquetas de leyenda se crean utilizando los nuevos valores del registro proporcionados.

### <a name="to-turn-off-the-smart-captioning-feature"></a>Para desactivar la característica de subtítulos (CC) inteligente

1.  Abra una ventana de comandos, haga clic en **iniciar** y, a continuación, **ejecutar**.

2.  Tipo de `regedit` en el **ejecutar** cuadro de diálogo y haga clic en **Aceptar**.

3.  Expanda el **HKEY_CURRENT_USER**, **Software**, **Microsoft**, **VisualStudio** nodo.

7.  Haga clic en el **15.0** nodo y crear un nuevo **clave** denominado `Data Designers`.

8.  Haga clic en el **diseñadores datos** nodo y crear tres nuevos valores de cadena:

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`

11. Haga clic en el **SmartCaptionExpression** de elemento y seleccione **modificar**.

12. Escriba `(.*)` para el valor. Esto coincidirá con la cadena completa.

13. Haga clic en el **SmartCaptionReplacement** de elemento y seleccione **modificar**.

14. Escriba `$1` para el valor. Esto reemplaza la cadena con el valor coincidente, que es la cadena completa de modo que permanecerán sin cambios.

    La próxima vez que se arrastran elementos desde la **orígenes de datos** las etiquetas de título de ventana, se crean con títulos sin modificar.

## <a name="see-also"></a>Vea también

- [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)