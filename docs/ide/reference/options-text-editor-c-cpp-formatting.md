---
title: Opciones, editor de texto, C/C++, formato | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.C%2fC%2b%2b.Formatting.General
dev_langs:
- C++
helpviewer_keywords:
- Text Editor Options dialog box, formatting
ms.assetid: cb6f1cbb-5305-48da-a8e8-33fd70775d46
caps.latest.revision: 16
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 41cca3051eaf1bfdc90f6616900699b8996033b0
ms.contentlocale: es-es
ms.lasthandoff: 05/24/2017

---
# <a name="options-text-editor-cc-formatting"></a>Opciones, editor de texto, C/C++, formato
Permite cambiar el comportamiento predeterminado del editor de código cuando se programa en C o C++.  
  
 Para tener acceso a esta página, en el cuadro de diálogo **Opciones**, en el panel izquierdo, expanda **Editor de texto**, expanda **C/C++** y, a continuación, haga clic en **Formato**.  
  
> [!NOTE]
>  Es posible que tu equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="cc-options"></a>Opciones de C/C++  
 **Habilitar información rápida sobre herramientas automática**  
 Habilita o deshabilita la característica de IntelliSense Información rápida.  
  
## <a name="inactive-code"></a>Código inactivo  
 **Mostrar bloques de código inactivos**  
 El código que está inactivo debido a las declaraciones `#ifdef` aparece con un color diferente para facilitar su identificación.  
  
 **Deshabilitar opacidad de código inactivo**  
 El código inactivo se puede identificar utilizando el color en lugar de la transparencia.  
  
 **Porcentaje de opacidad del código inactivo**  
 Se puede personalizar el grado de opacidad de los bloques de código inactivos.  
  
## <a name="indentation"></a>Sangría  
 **Aplicar sangría a las llaves**  
 Puede configurar cómo se alinean las llaves cuando se presiona ENTRAR después de comenzar un bloque de código, por ejemplo, una función o un bucle `for`. Las llaves pueden estar alineadas con el primer carácter del bloque de código o con sangría.  
  
 **Sangría automática con tecla TAB**  
 Puede configurar lo que ocurre en la línea de código actual al presionar TAB. Se aplica sangría a la línea o bien se inserta un carácter de tabulación.  
  
## <a name="miscellaneous"></a>Varios  
 **Enumerar comentarios en la ventana Lista de tareas**  
 El editor puede analizar archivos de código fuente abiertos para buscar palabras preestablecidas en los comentarios. Crea una entrada en la ventana **Lista de tareas** para todas las palabras clave que encuentra.  
  
 **Resaltar tokens de emparejamiento**  
 Cuando se coloca el cursor junto a una llave, el editor puede resaltar la llave correspondiente de modo que pueda ver el código incluido entre llaves más fácilmente.  
  
## <a name="outlining"></a>Esquematización  
 **Especificar el modo de esquematización al abrir los archivos**  
 Cuando se coloca un archivo en el editor de texto, se puede habilitar la característica de esquematización. Para obtener más información, vea [Esquematización](../../ide/outlining.md). Cuando esta opción está seleccionada, la característica de esquematización se habilita al abrir un archivo.  
  
 **Esquematizar automáticamente bloques de regiones pragma**  
 Cuando esta opción está seleccionada, se habilita la esquematización automática de las [directivas pragma](/cpp/preprocessor/pragma-directives-and-the-pragma-keyword). Esto permite expandir o contraer bloques de región pragma en modo de esquematización.  
  
 **Esquematizar automáticamente bloques de instrucciones**  
 Al seleccionar esta opción, se habilita la esquematización automática de las construcciones de instrucción siguientes:  
  
-   [if-else](/dotnet/csharp/language-reference/keywords/if-else)  
  
-   [switch (Instrucción) (C++)](/cpp/cpp/switch-statement-cpp)  
  
-   [while (Instrucción) (C++)](/cpp/cpp/while-statement-cpp)  
  
## <a name="see-also"></a>Vea también  
 [General, Entorno, Opciones (Cuadro de diálogo)](../../ide/reference/general-environment-options-dialog-box.md)   
 [Usar IntelliSense](../../ide/using-intellisense.md)
