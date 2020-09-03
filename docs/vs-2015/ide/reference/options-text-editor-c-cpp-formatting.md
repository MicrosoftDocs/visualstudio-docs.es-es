---
title: Opciones, editor de texto, C-C++, formato | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5ad06dfb32c301985eb4976f6c89c7be1e0e68da
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662340"
---
# <a name="options-text-editor-cc-formatting"></a>Opciones, editor de texto, C/C++, formato
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Permite cambiar el comportamiento predeterminado del editor de código cuando se programa en C o C++.

 Para tener acceso a esta página, en el cuadro de diálogo **Opciones**, en el panel izquierdo, expanda **Editor de texto**, expanda **C/C++** y, a continuación, haga clic en **Formato**.

> [!NOTE]
> Es posible que tu equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para obtener más información, consulte [Personalizar la configuración de desarrollo de Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="cc-options"></a>Opciones de C/C++
 **Habilitar información sobre herramientas de información rápida automática** Habilita o deshabilita la característica IntelliSense de información rápida.

## <a name="inactive-code"></a>Código inactivo
 **Mostrar bloques de código inactivos** El código que está inactivo debido a las `#ifdef` declaraciones se colorea de manera diferente para ayudarle a identificarlo.

 **Deshabilitar opacidad de código inactivo** El código inactivo se puede identificar utilizando el color en lugar de la transparencia.

 **Porcentaje de opacidad de código inactivo** Se puede personalizar el grado de opacidad de los bloques de código inactivos.

## <a name="indentation"></a>Sangría
 **Aplicar sangría** a las llaves Puede configurar cómo se alinean las llaves al presionar entrar después de comenzar un bloque de código, por ejemplo, una función o un `for` bucle. Las llaves pueden estar alineadas con el primer carácter del bloque de código o con sangría.

 **Sangría automática en la pestaña** Puede configurar lo que ocurre en la línea de código actual al presionar TAB. Se aplica sangría a la línea o bien se inserta un carácter de tabulación.

## <a name="miscellaneous"></a>Varios
 **Enumerar los comentarios en la ventana de lista de tareas** El editor puede analizar archivos de código fuente abiertos para buscar palabras preestablecidas en los comentarios. Crea una entrada en la ventana **Lista de tareas** para todas las palabras clave que encuentra.

 **Resaltar tokens coincidentes** Cuando el cursor está junto a una llave, el editor puede resaltar la llave correspondiente para que pueda ver más fácilmente el código contenido.

## <a name="outlining"></a>esquematizar
 **Especificar el modo de esquematización al abrir los archivos** Al colocar un archivo en el editor de texto, puede habilitar la característica de esquematización. Para obtener más información, vea [Esquematización](../../ide/outlining.md). Cuando esta opción está seleccionada, la característica de esquematización se habilita al abrir un archivo.

 **Esquematización automática de bloques de región de #pragma** Cuando se selecciona esta opción, se habilita la esquematización automática para [directivas pragma](https://msdn.microsoft.com/library/9867b438-ac64-4e10-973f-c3955209873f) . Esto permite expandir o contraer bloques de región pragma en modo de esquematización.

 **Esquematización automática de bloques de instrucciones** Cuando se selecciona esta opción, se habilita la esquematización automática para las siguientes construcciones de instrucción:

- [if-else](https://msdn.microsoft.com/library/d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2)

- [Switch (instrucción) (C++)](https://msdn.microsoft.com/library/6c3f3ed3-5593-463c-8f4b-b33742b455c6)

- [while (Instrucción) (C++)](https://msdn.microsoft.com/library/358dbe76-5e5e-4af5-b575-c2293c636899)

## <a name="see-also"></a>Consulte también
 [General, entorno, opciones (cuadro de diálogo)](../../ide/reference/general-environment-options-dialog-box.md) [con IntelliSense](../../ide/using-intellisense.md)
