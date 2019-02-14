---
title: Opciones, editor de texto, C/C++, formato | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.C%2fC%2b%2b.Formatting.General
dev_langs:
- C++
helpviewer_keywords:
- Text Editor Options dialog box, formatting
ms.assetid: cb6f1cbb-5305-48da-a8e8-33fd70775d46
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 767bb04bcfe14c8cafbe69e5cb19ecbd8082ee40
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54770644"
---
# <a name="options-text-editor-cc-formatting"></a>Opciones, editor de texto, C/C++, formato
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Permite cambiar el comportamiento predeterminado del editor de código cuando se programa en C o C++.  
  
 Para tener acceso a esta página, en el cuadro de diálogo **Opciones**, en el panel izquierdo, expanda **Editor de texto**, expanda **C/C++** y, a continuación, haga clic en **Formato**.  
  
> [!NOTE]
>  Es posible que el equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
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
  
## <a name="outlining"></a>esquematizar  
 **Especificar el modo de esquematización al abrir los archivos**  
 Cuando se coloca un archivo en el editor de texto, se puede habilitar la característica de esquematización. Para obtener más información, vea [Esquematización](../../ide/outlining.md). Cuando esta opción está seleccionada, la característica de esquematización se habilita al abrir un archivo.  
  
 **Esquematizar automáticamente bloques de regiones pragma**  
 Cuando esta opción está seleccionada, se habilita la esquematización automática de las [directivas pragma](http://msdn.microsoft.com/library/9867b438-ac64-4e10-973f-c3955209873f). Esto permite expandir o contraer bloques de región pragma en modo de esquematización.  
  
 **Esquematizar automáticamente bloques de instrucciones**  
 Al seleccionar esta opción, se habilita la esquematización automática de las construcciones de instrucción siguientes:  
  
-   [if-else](http://msdn.microsoft.com/library/d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2)  
  
-   [switch (Instrucción) (C++)](http://msdn.microsoft.com/library/6c3f3ed3-5593-463c-8f4b-b33742b455c6)  
  
-   [while (Instrucción) (C++)](http://msdn.microsoft.com/library/358dbe76-5e5e-4af5-b575-c2293c636899)  
  
## <a name="see-also"></a>Vea también  
 [General, Entorno, Opciones (Cuadro de diálogo)](../../ide/reference/general-environment-options-dialog-box.md)   
 [Usar IntelliSense](../../ide/using-intellisense.md)
