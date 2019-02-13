---
title: Configuración de compilación avanzada (Cuadro de diálogo, C#)
ms.date: 06/20/2017
ms.topic: reference
f1_keywords:
- cs.AdvancedBuildSettings
helpviewer_keywords:
- Build options [C#], advanced
ms.assetid: 141f2dee-1563-4ce6-ba37-32920b082519
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a668e64f6b8a10cf22e08575ca9c2df385131666
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55930472"
---
# <a name="advanced-build-settings-dialog-box-c"></a>Configuración de compilación avanzada (Cuadro de diálogo, C#)

Use el cuadro de diálogo **Configuración de compilación avanzada** del **Diseñador de proyectos** para especificar las propiedades de configuración de compilación avanzada del proyecto. Este cuadro de diálogo solo se aplica a proyectos de [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)].

## <a name="general"></a>General

Las opciones siguientes le permiten establecer la configuración avanzada general.

**Versión de lenguaje**

Especifica la versión del idioma que se va a usar. El conjunto de características es diferente en cada versión, por lo que esta opción se puede usar para forzar al compilador a que permita solo un subconjunto de las características implementadas, o para habilitar solo las características compatibles con un estándar existente. Esta configuración tiene las siguientes opciones:

- **default**

   Se dirige a la versión actual.

- **ISO-1** e **ISO-2**

   Se dirige a las características estándar de ISO-1 e ISO-2, respectivamente.

- **C# [número de versión]**

   Se dirige a una versión específica de C#. Para obtener más información, consulte [/langversion (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option).

**Informe de errores internos del compilador**

Especifica si se deben notificar los errores del compilador a Microsoft. Si se establece en **aviso** (valor predeterminado), recibirá un aviso si se produce un error interno del compilador, lo que le ofrece la opción de enviar electrónicamente un informe de errores a Microsoft. Si se establece en **enviar**, se enviará automáticamente un informe de errores. Si se establece en **cola**, se pondrán en cola los informes de errores. Si se establece en **ninguno**, el error se notificará solo en la salida de texto del compilador. Para obtener más información, consulte [/errorreport (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option).

**Comprobar el desbordamiento y subdesbordamiento aritmético**

Especifica si una instrucción aritmética de enteros que no está en el ámbito de las palabras clave [checked](/dotnet/csharp/language-reference/keywords/checked) o [unchecked](/dotnet/csharp/language-reference/keywords/unchecked) y que produce un valor fuera del intervalo del tipo de datos provocará una excepción en tiempo de ejecución. Para obtener más información, consulte [/checked (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option).

**No hacer referencia a mscorlib.dll**

Especifica si se importará mscorlib.dll al programa, definiendo la totalidad del espacio de nombres <xref:System>. Active esta casilla si quiere definir o crear sus propios objetos y espacios de nombres <xref:System>. Para obtener más información, consulte [/nostdlib (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option).

## <a name="output"></a>Salida

Las opciones siguientes le permiten especificar opciones de salida avanzadas.

**Información de depuración**

Especifica el tipo de información de depuración generado por el compilador. Para obtener información sobre cómo configurar el rendimiento de depuración de una aplicación, consulte [Facilitar la depuración de una imagen](/dotnet/framework/debug-trace-profile/making-an-image-easier-to-debug). Esta configuración tiene las siguientes opciones:

- **none**

   Especifica que no se generará ninguna información de depuración.

- **full**

   Permite asociar un depurador al programa en ejecución.

- **pdbonly**

   Permite depurar el código fuente cuando el programa se inicia en el depurador, pero solo mostrará el ensamblador cuando el programa que se ejecuta está asociado al depurador.

-  **portable**

   Genera un archivo .PDB, un archivo de símbolos portátil no específico de plataforma que proporciona a otras herramientas, especialmente depuradores, información sobre qué se encuentra en el archivo ejecutable principal y cómo se ha generado. Vea [PDB portátil](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md) para obtener más información.

- **embedded**

   Inserta información de símbolos portátil en el ensamblado. No se genera ningún archivo .PDB externo.

Para obtener más información, consulte [/debug (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option).

**Alineación de archivo**

Especifica el tamaño de las secciones del archivo de salida. Los valores válidos son **512**, **1024**, **2048**, **4096** y **8192**. Estos valores se miden en bytes. Cada sección se alineará en un límite que es un múltiplo de este valor, lo que afecta al tamaño del archivo de salida. Para obtener más información, consulte [/filealign (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option).

**Dirección base de biblioteca**

Especifica la dirección base preferida para cargar una DLL. La dirección base predeterminada para un archivo DLL se establece mediante [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)] Common Language Runtime. Para obtener más información, consulte [/baseaddress (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option).

## <a name="see-also"></a>Vea también

- [Opciones del compilador de C#](/dotnet/csharp/language-reference/compiler-options/index)
- [Página Compilar (Diseñador de proyectos) (C#)](../../ide/reference/build-page-project-designer-csharp.md)