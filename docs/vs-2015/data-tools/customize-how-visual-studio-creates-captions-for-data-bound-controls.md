---
title: Personalizar cómo Visual Studio crea los títulos de controles enlazados a datos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b6906e68c74bbb718f9bfc041ab35075b3f9b0aa
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/29/2018
ms.locfileid: "50220191"
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>Personalizar el modo en que Visual Studio crea los títulos de controles enlazados a datos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Cuando se arrastran elementos desde la [ventana Orígenes de datos](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) en el Diseñador de Windows Forms, una consideración especial entra en juego: se cambian los nombres de columna en las etiquetas de leyenda en una cadena más legible cuando dos o más palabras están se encontró que se concatenan juntos. Puede personalizar la manera en que se crean estas etiquetas, estableciendo el **SmartCaptionExpression**, **SmartCaptionReplacement**, y **SmartCaptionSuffix** valores en el **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Data diseñadores** clave del registro.  
  
> [!NOTE]
>  Esta clave del registro no existe hasta que la cree.  
  
 Etiquetas inteligentes se controla mediante la expresión regular especificada en el valor de la **SmartCaptionExpression** valor. Agregar el **diseñadores de datos** clave del registro invalida la expresión regular predeterminada que controla las etiquetas de leyenda. Para obtener más información sobre las expresiones regulares, vea [usar expresiones regulares en Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
 En la tabla siguiente se describe los valores del registro que controlan las etiquetas de leyenda.  
  
|Elemento del registro|Descripción|  
|-------------------|-----------------|  
|**SmartCaptionExpression**|La expresión regular que se usa para hacer coincidir los patrones.|  
|**SmartCaptionReplacement**|El formato para mostrar cualquier grupo que coincide en el **SmartCaptionExpression**.|  
|**SmartCaptionSuffix**|Una cadena opcional que se anexará al final de la leyenda.|  
  
 La tabla siguiente muestra la configuración predeterminada interna para estos valores del registro.  
  
|Elemento del registro|Valor predeterminado|Explicación|  
|-------------------|-------------------|-----------------|  
|**SmartCaptionExpression**|(\\\p{Ll}) (\\\p{Lu})&#124;_ +|Coincide con un carácter en minúscula seguido por un carácter en mayúscula o un carácter de subrayado.|  
|**SmartCaptionReplacement**|$1 $2|$1 representa cualquier carácter coincidente en el primer paréntesis de la expresión y $2 representa cualquier carácter coincidente en el segundo paréntesis. La sustitución es la primera coincidencia, un espacio y, a continuación, la segunda coincidencia.|  
|**SmartCaptionSuffix**|:|Representa un carácter que se anexa a la cadena devuelta. Por ejemplo, si el título es `Company Name`, el sufijo facilita `Company Name:`|  
  
> [!CAUTION]
>  Debe tener mucho cuidado al hacer nada en el Editor del registro. Realizar una copia de seguridad del registro antes de editarlo. Si utiliza incorrectamente el Editor del registro, puede provocar problemas graves que quizás requieran reinstalar el sistema operativo. Microsoft no garantiza que se pueden resolver los problemas que provocan utilizando el Editor del Registro incorrectamente. Utilice el Editor del registro bajo su propia responsabilidad.  
>   
>  El siguiente artículo de Knowledge Base contiene instrucciones para realizar copias de seguridad, editar y restaurar el registro: [descripción del registro de Microsoft Windows](http://support.microsoft.com/default.aspx?scid=kb;en-us;256986) (http://support.microsoft.com/default.aspx?scid=kb; en-us; 256986)  
  
### <a name="to-modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>Para modificar el comportamiento inteligente subtítulos (CC) de la ventana de orígenes de datos  
  
1.  Abra una ventana de comandos, haga clic en **iniciar** y, a continuación, **ejecutar**.  
  
2.  Tipo `regedit` en el **ejecutar** cuadro de diálogo y haga clic en **Aceptar**.  
  
3.  Expanda el **HKEY_CURRENT_USER** nodo.  
  
4.  Expanda el **Software** nodo.  
  
5.  Expanda el **Microsoft** nodo.  
  
6.  Expanda el **VisualStudio** nodo.  
  
7.  Haga clic en el **10.0** nodo y crear un nuevo **clave** denominado `Data Designers`.  
  
8.  Haga clic en el **diseñadores de datos** nodo y crear un nuevo **valor de cadena** denominado `SmartCaptionExpression`.  
  
9. Haga clic en el **diseñadores de datos** nodo y crear un nuevo **valor de cadena** denominado `SmartCaptionReplacement`.  
  
10. Haga clic en el **diseñadores de datos** nodo y crear un nuevo **valor de cadena** denominado `SmartCaptionSuffix`.  
  
11. Haga clic en el **SmartCaptionExpression** de elemento y seleccione **modificar**.  
  
12. Escriba la expresión regular que desee la **orígenes de datos** ventana para utilizar.  
  
13. Haga clic en el **SmartCaptionReplacement** de elemento y seleccione **modificar**.  
  
14. Escriba el reemplazo de cadena con formato de la manera en que desea mostrar los modelos que coinciden en la expresión regular.  
  
15. Haga clic en el **SmartCaptionSuffix** de elemento y seleccione **modificar**.  
  
16. Escriba los caracteres que desea que aparezcan al final de la leyenda.  
  
     La próxima vez que se arrastran elementos desde la **orígenes de datos** ventana, las etiquetas de leyenda se crean con los nuevos valores del registro proporcionados.  
  
### <a name="to-turn-off-the-smart-captioning-feature"></a>Para desactivar la característica smart subtítulos (CC)  
  
1.  Abra una ventana de comandos, haga clic en **iniciar** y, a continuación, **ejecutar**.  
  
2.  Tipo `regedit` en el **ejecutar** cuadro de diálogo y haga clic en **Aceptar**.  
  
3.  Expanda el **HKEY_CURRENT_USER** nodo.  
  
4.  Expanda el **Software** nodo.  
  
5.  Expanda el **Microsoft** nodo.  
  
6.  Expanda el **VisualStudio** nodo.  
  
7.  Haga clic en el **10.0** nodo y crear un nuevo **clave** denominado `Data Designers`.  
  
8.  Haga clic en el **diseñadores de datos** nodo y crear un nuevo **valor de cadena** denominado `SmartCaptionExpression`.  
  
9. Haga clic en el **diseñadores de datos** nodo y crear un nuevo **valor de cadena** denominado `SmartCaptionReplacement`.  
  
10. Haga clic en el **diseñadores de datos** nodo y crear un nuevo **valor de cadena** denominado `SmartCaptionSuffix`.  
  
11. Haga clic en el **SmartCaptionExpression** de elemento y seleccione **modificar**.  
  
12. Escriba `(.*)` para el valor. Esto coincidirá con la cadena completa.  
  
13. Haga clic en el **SmartCaptionReplacement** de elemento y seleccione **modificar**.  
  
14. Escriba `$1` para el valor. Esto reemplaza la cadena con el valor coincidente, que es la cadena completa para que lo permanecerá sin cambios.  
  
     La próxima vez que se arrastran elementos desde la **orígenes de datos** las etiquetas de leyenda de ventana, se crean con títulos sin modificar.  
  
## <a name="see-also"></a>Vea también  
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)

