---
title: Personalizar títulos para los controles enlazados a datos
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
ms.openlocfilehash: 11f7249f30b1866ca7c4aea4bbefa850a5353c0f
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305590"
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>Personalizar el modo en que Visual Studio crea los títulos de controles enlazados a datos

Cuando se arrastran elementos desde la [ventana Orígenes de datos](add-new-data-sources.md#data-sources-window) a un diseñador, una consideración especial entra en juego: se cambian los nombres de columna en las etiquetas de leyenda en una cadena más legible cuando dos o más palabras se encuentran concatenados. Puede personalizar la manera en que se crean estas etiquetas, estableciendo el **SmartCaptionExpression**, **SmartCaptionReplacement**, y **SmartCaptionSuffix** valores en el **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Data diseñadores** clave del registro.

> [!NOTE]
> Esta clave del registro no existe hasta que la cree.

Etiquetas inteligentes se controla mediante la expresión regular especificada en el valor de la **SmartCaptionExpression** valor. Agregar el **diseñadores de datos** clave del registro invalida la expresión regular predeterminada que controla las etiquetas de leyenda. Para obtener más información sobre las expresiones regulares, vea [mediante expresiones regulares en Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

En la tabla siguiente se describe los valores del registro que controlan las etiquetas de leyenda.

|Elemento del registro|Descripción|
|-------------------|-----------------|
|**SmartCaptionExpression**|La expresión regular que se usa para que coincida con los patrones.|
|**SmartCaptionReplacement**|El formato para mostrar cualquier grupo que coincide en el **SmartCaptionExpression**.|
|**SmartCaptionSuffix**|Una cadena opcional que se anexará al final de la leyenda.|

La tabla siguiente muestra la configuración predeterminada interna para estos valores del registro.

|Elemento del registro|Valor predeterminado|Explicación|
|-------------------|-------------------|-----------------|
|**SmartCaptionExpression**|**(\\\p{Ll}) (\\\p{Lu})&#124;_ +**|Coincide con un carácter en minúscula seguido por un carácter en mayúscula o un carácter de subrayado.|
|**SmartCaptionReplacement**|"$1"|El **$1** representa cualquier carácter coincidente en el primer paréntesis de la expresión y el **$2** representa cualquier carácter coincidente en el segundo paréntesis. La sustitución es la primera coincidencia, un espacio y, a continuación, la segunda coincidencia.|
|**SmartCaptionSuffix**|**:**|Representa un carácter que se anexa a la cadena devuelta. Por ejemplo, si el título es `Company Name`, el sufijo facilita `Company Name:`|

> [!CAUTION]
> Debe tener mucho cuidado al hacer nada en el Editor del registro. Realizar una copia de seguridad del registro antes de editarlo. Si utiliza incorrectamente el Editor del registro, puede provocar problemas graves que quizás requieran reinstalar el sistema operativo. Microsoft no garantiza que se pueden resolver los problemas que provocan utilizando el Editor del Registro incorrectamente. Utilice el Editor del registro bajo su propia responsabilidad.
>
> El siguiente artículo de Knowledge Base contiene instrucciones para realizar copias de seguridad, editar y restaurar el registro: [descripción del registro de Microsoft Windows](http://support.microsoft.com/default.aspx?scid=kb;en-us;256986) (http://support.microsoft.com/default.aspx?scid=kb; en-us; 256986)

## <a name="modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>Modificar el comportamiento inteligente subtítulos (CC) de la ventana de orígenes de datos

1.  Abra una ventana de comandos, haga clic en **iniciar** y, a continuación, **ejecutar**.

2.  Tipo `regedit` en el **ejecutar** cuadro de diálogo y haga clic en **Aceptar**.

3.  Expanda el **HKEY_CURRENT_USER** > **Software** > **Microsoft** > **VisualStudio**nodo.

4.  Haga clic en el **15.0** nodo y crear un nuevo **clave** denominado `Data Designers`.

5.  Haga clic en el **diseñadores de datos** nodo y crear tres nuevos valores de cadena:

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`

6. Haga clic en el **SmartCaptionExpression** valor y seleccione **modificar**.

7. Escriba la expresión regular que desee la **orígenes de datos** ventana para utilizar.

8. Haga clic en el **SmartCaptionReplacement** valor y seleccione **modificar**.

9. Escriba el reemplazo de cadena con formato de la manera en que desea mostrar los modelos que coinciden en la expresión regular.

10. Haga clic en el **SmartCaptionSuffix** valor y seleccione **modificar**.

11. Escriba los caracteres que desea que aparezcan al final de la leyenda.

    La próxima vez que se arrastran elementos desde la **orígenes de datos** ventana, las etiquetas de leyenda se crean con los nuevos valores del registro proporcionados.

## <a name="turn-off-the-smart-captioning-feature"></a>Desactivar la característica smart subtítulos (CC)

1.  Abra una ventana de comandos, haga clic en **iniciar** y, a continuación, **ejecutar**.

2.  Tipo `regedit` en el **ejecutar** cuadro de diálogo y haga clic en **Aceptar**.

3.  Expanda el **HKEY_CURRENT_USER** > **Software** > **Microsoft** > **VisualStudio**nodo.

4.  Haga clic en el **15.0** nodo y crear un nuevo **clave** denominado `Data Designers`.

5.  Haga clic en el **diseñadores de datos** nodo y crear tres nuevos valores de cadena:

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`

6. Haga clic en el **SmartCaptionExpression** de elemento y seleccione **modificar**.

7. Escriba `(.*)` para el valor. Esto coincidirá con la cadena completa.

8. Haga clic en el **SmartCaptionReplacement** de elemento y seleccione **modificar**.

9. Escriba `$1` para el valor. Esto reemplaza la cadena con el valor coincidente, que es la cadena completa para que lo permanecerá sin cambios.

    La próxima vez que se arrastran elementos desde la **orígenes de datos** las etiquetas de leyenda de ventana, se crean con títulos sin modificar.

## <a name="see-also"></a>Vea también

- [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)