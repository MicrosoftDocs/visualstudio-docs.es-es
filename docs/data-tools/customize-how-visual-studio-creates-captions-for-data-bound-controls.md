---
title: "C&#243;mo: Personalizar el modo en que Visual Studio crea los t&#237;tulos de controles enlazados a datos | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "títulos, enlazadas a datos"
  - "Orígenes de datos (ventana), títulos de etiquetas"
  - "títulos de etiquetas, Orígenes de datos (ventana)"
  - "títulos inteligentes"
ms.assetid: 6d4d15f8-4d78-42fd-af64-779ae98d62c8
caps.latest.revision: 12
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Personalizar el modo en que Visual Studio crea los t&#237;tulos de controles enlazados a datos
Cuando se arrastran elementos desde [Orígenes de datos \(ventana\)](../Topic/Data%20Sources%20Window.md) al diseñador de Windows Forms debe tenerse en cuenta una consideración especial: los nombres de columna de las etiquetas de leyenda cambian el formato a una cadena más legible cuando dos o más palabras están concatenadas.  Puede personalizar la forma en que se crean estas etiquetas estableciendo los valores **SmartCaptionExpression**, **SmartCaptionReplacement** y **SmartCaptionSuffix** en la clave del Registro **HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\10.0\\Data Designers**.  
  
> [!NOTE]
>  Esta clave del Registro no existe hasta que la cree.  
  
 La generación de etiquetas inteligentes se controla mediante la expresión regular escrita en el valor de **SmartCaptionExpression**.  Al agregar la clave del Registro **Data Designers**, se invalida la expresión regular predeterminada que controla las etiquetas de leyenda.  Para obtener más información acerca de las expresiones regulares, vea [Usar expresiones regulares en Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
 En la siguiente tabla se describen los valores del Registro que controlan las etiquetas de leyenda.  
  
|Elemento de Registro|Descripción|  
|--------------------------|-----------------|  
|SmartCaptionExpression|La expresión regular que se utiliza para hacer coincidir los modelos.|  
|SmartCaptionReplacement|El formato para mostrar cualquier grupo que coincide en **SmartCaptionExpression**.|  
|SmartCaptionSuffix|Una cadena opcional para anexar al final de la leyenda.|  
  
 En las tablas siguientes se incluye la configuración predeterminada interna para estos valores del Registro.  
  
|Elemento|Valor predeterminado|Explicación|  
|--------------|--------------------------|-----------------|  
|**SmartCaptionExpression**|\(\\\\p{Ll}\)\(\\\\p{Lu}\)&#124;\_\+|Coincide con un carácter en minúscula seguido por un carácter en mayúscula o un subrayado.|  
|**SmartCaptionReplacement**|$1 $2|$1 representa cualquier carácter que coincide en los primeros paréntesis de la expresión y $2 representa cualquier carácter que coincide en los segundos paréntesis.  El reemplazo es la primera coincidencia, un espacio, y a continuación la segunda coincidencia.|  
|**SmartCaptionSuffix**|:|Representa un carácter anexado a la cadena devuelta.  Por ejemplo, si la leyenda es `Company Name`, el sufijo la convierte en `Company Name:`|  
  
> [!CAUTION]
>  Debe extremar las precauciones al realizar cambios en el Editor del Registro.  Realice una copia de seguridad del Registro antes de editarlo.  El uso incorrecto del Editor del Registro puede causar problemas graves que obliguen a reinstalar el sistema operativo.  Microsoft no garantiza que se puedan resolver los problemas que produce la utilización incorrecta del Editor del Registro.  Utilice el Editor del registro bajo su propia responsabilidad.  
>   
>  El siguiente artículo de KnowledgeBase contiene instrucciones para realizar una copia de seguridad, editar y restaurar el Registro: [Descripción del Registro de Microsoft Windows](http://support.microsoft.com/default.aspx?scid=kb;en-us;256986) \(http:\/\/support.microsoft.com\/default.aspx?scid\=kb;en\-us;256986\)  
  
### Para modificar el comportamiento de los títulos inteligentes de la ventana Orígenes de datos  
  
1.  Abra una ventana de comandos haciendo clic en **Iniciar** y, a continuación, en **Ejecutar**.  
  
2.  Escriba `regedit` en el cuadro de diálogo **Ejecutar** y haga clic en **Aceptar**.  
  
3.  Expanda el nodo **HKEY\_CURRENT\_USER**.  
  
4.  Expanda el nodo **Software**.  
  
5.  Expanda el nodo **Microsoft**.  
  
6.  Expanda el nodo **VisualStudio**.  
  
7.  Haga clic con el botón secundario en el nodo **10.0** y cree una nueva **Clave** denominada `Data Designers`.  
  
8.  Haga clic con el botón secundario en el nodo **Data Designers** y cree un nuevo **Valor de cadena** denominado `SmartCaptionExpression`.  
  
9. Haga clic con el botón secundario en el nodo **Data Designers** y cree un nuevo **Valor de cadena** denominado `SmartCaptionReplacement`.  
  
10. Haga clic con el botón secundario en el nodo **Data Designers** y cree un nuevo **Valor de cadena** denominado `SmartCaptionSuffix`.  
  
11. Haga clic con el botón secundario en el elemento **SmartCaptionExpression** y elija **Modificar**.  
  
12. Escriba la expresión regular que desea que utilice la ventana **Orígenes de datos**.  
  
13. Haga clic con el botón secundario en el elemento **SmartCaptionReplacement** y elija **Modificar**.  
  
14. Escriba la cadena de reemplazo con el formato en que desea mostrar los modelos que coinciden en la expresión regular.  
  
15. Haga clic con el botón secundario en el elemento **SmartCaptionSuffix** y elija **Modificar**.  
  
16. Escriba cualquier carácter que desea mostrar al final de la leyenda.  
  
     La próxima vez que arrastra elementos desde la ventana **Orígenes de datos**, las etiquetas de leyenda se crean utilizando los nuevos valores del Registro proporcionados.  
  
### Para desactivar la característica de títulos inteligentes  
  
1.  Abra una ventana de comandos haciendo clic en **Iniciar** y, a continuación, en **Ejecutar**.  
  
2.  Escriba `regedit` en el cuadro de diálogo **Ejecutar** y haga clic en **Aceptar**.  
  
3.  Expanda el nodo **HKEY\_CURRENT\_USER**.  
  
4.  Expanda el nodo **Software**.  
  
5.  Expanda el nodo **Microsoft**.  
  
6.  Expanda el nodo **VisualStudio**.  
  
7.  Haga clic con el botón secundario en el nodo **10.0** y cree una nueva **Clave** denominada `Data Designers`.  
  
8.  Haga clic con el botón secundario en el nodo **Data Designers** y cree un nuevo **Valor de cadena** denominado `SmartCaptionExpression`.  
  
9. Haga clic con el botón secundario en el nodo **Data Designers** y cree un nuevo **Valor de cadena** denominado `SmartCaptionReplacement`.  
  
10. Haga clic con el botón secundario en el nodo **Data Designers** y cree un nuevo **Valor de cadena** denominado `SmartCaptionSuffix`.  
  
11. Haga clic con el botón secundario en el elemento **SmartCaptionExpression** y elija **Modificar**.  
  
12. Escriba `(.*)` para el valor.  Esto coincidirá con la cadena completa.  
  
13. Haga clic con el botón secundario en el elemento **SmartCaptionReplacement** y elija **Modificar**.  
  
14. Escriba `(.*)` para el valor.  Esto reemplaza la cadena con el valor coincidido, que es la cadena completa; de esta forma permanece sin modificar.  
  
     La próxima vez que arrastra elementos desde la ventana **Orígenes de datos**, las etiquetas de leyenda se crean con leyendas sin modificar.  
  
## Vea también  
 [Expresiones regulares de .NET Framework](../Topic/.NET%20Framework%20Regular%20Expressions.md)   
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Preparar la aplicación para recibir datos](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Buscar datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modificar datos en la aplicación](../data-tools/editing-data-in-your-application.md)   
 [Validar datos](../Topic/Validating%20Data.md)   
 [Guardar datos](../data-tools/saving-data.md)