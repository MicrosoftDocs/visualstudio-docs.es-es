---
title: "Configuración de compilación avanzada (Cuadro de diálogo, C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cs.AdvancedBuildSettings
helpviewer_keywords:
- Build options [C#], advanced
ms.assetid: 141f2dee-1563-4ce6-ba37-32920b082519
caps.latest.revision: 13
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
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 82ec5d2db35da72beb017e15d1c271f751b5f56b
ms.lasthandoff: 02/22/2017

---
# <a name="advanced-build-settings-dialog-box-c"></a>Configuración de compilación avanzada (Cuadro de diálogo, C#)
Use el cuadro de diálogo **Configuración de compilación avanzada** del **Diseñador de proyectos** para especificar las propiedades de configuración de compilación avanzada del proyecto. Este cuadro de diálogo solo se aplica a proyectos de [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)].  
  
## <a name="general"></a>General  
 Las opciones siguientes le permiten establecer la configuración avanzada general.  
  
 **Versión de lenguaje**  
 Especifica la versión del idioma que se va a usar. El conjunto de características es diferente en cada versión, por lo que esta opción se puede usar para forzar al compilador a que permita solo un subconjunto de las características implementadas, o para habilitar solo las características compatibles con un estándar existente. Esta configuración tiene las siguientes opciones:  
  
-   **ISO-1**  
  
     Se dirige a las características estándar de ISO-1.  
  
-   **default**  
  
     Se dirige a la versión actual.  
  
 Para obtener más información, consulte [/langversion (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option).  
  
 **Informe de errores internos del compilador**  
 Especifica si se deben notificar los errores del compilador a Microsoft. Si se establece en **aviso** (valor predeterminado), recibirá un aviso si se produce un error interno del compilador, lo que le ofrece la opción de enviar electrónicamente un informe de errores a Microsoft. Si se establece en **enviar**, se enviará automáticamente un informe de errores. Si se establece en **cola**, se pondrán en cola los informes de errores. Si se establece en **ninguno**, el error se notificará solo en la salida de texto del compilador. Para obtener más información, consulte [/errorreport (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option).  
  
 **Comprobar el desbordamiento y subdesbordamiento aritmético**  
 Especifica si una instrucción aritmética de enteros que no está en el ámbito de las palabras clave [checked](/dotnet/csharp/language-reference/keywords/checked) o [unchecked](/dotnet/csharp/language-reference/keywords/unchecked) y que produce un valor fuera del intervalo del tipo de datos provocará una excepción en tiempo de ejecución. Para obtener más información, consulte [/checked (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option).  
  
 **No hacer referencia a mscorlib.dll**  
 Especifica si se importará mscorlib.dll al programa, definiendo la totalidad del espacio de nombres <xref:System>. Active esta casilla si quiere definir o crear sus propios objetos y espacios de nombres <xref:System>. Para obtener más información, consulte [/nostdlib (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option).  
  
## <a name="output"></a>Salida  
 Las opciones siguientes le permiten especificar opciones de salida avanzadas.  
  
 **Información de depuración**  
 Especifica el tipo de información de depuración generado por el compilador. Para obtener información sobre cómo configurar el rendimiento de depuración de una aplicación, consulte [Facilitar la depuración de una imagen](http://msdn.microsoft.com/Library/7d90ea7a-150f-4f97-98a7-f9c26541b9a3). Esta configuración tiene las siguientes opciones:  
  
-   **none**  
  
     Especifica que no se generará ninguna información de depuración  
  
-   **full**  
  
     Permite asociar un depurador al programa en ejecución.  
  
-   **pdbonly**  
  
     Permite depurar el código fuente cuando el programa se inicia en el depurador, pero solo mostrará el ensamblador cuando el programa que se ejecuta está asociado al depurador.  
  
 Para obtener más información, consulte [/debug (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option).  
  
 **Alineación de archivo**  
 Especifica el tamaño de las secciones del archivo de salida. Los valores válidos son **512**, **1024**, **2048**, **4096** y **8192**. Estos valores se miden en bytes. Cada sección se alineará en un límite que es un múltiplo de este valor, lo que afecta al tamaño del archivo de salida. Para obtener más información, consulte [/filealign (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option).  
  
 **Dirección base del archivo DLL**  
 Especifica la dirección base preferida para cargar una DLL. La dirección base predeterminada para un archivo DLL se establece mediante [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)] Common Language Runtime. Para obtener más información, consulte [/baseaddress (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option).  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador de C#](/dotnet/csharp/language-reference/compiler-options/index)   
 [Página Compilar (Diseñador de proyectos) (C#)](../../ide/reference/build-page-project-designer-csharp.md)
