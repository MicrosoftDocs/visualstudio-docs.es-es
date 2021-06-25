---
title: Marcas de Command-Line del compilador vsct | Microsoft Docs
description: El Visual Studio tabla de comandos proporciona opciones de línea de comandos para garantizar una compilación correcta de los archivos .vsct.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT files, compiling
- command-table file compilation (VSCT files)
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ce83df56e1bcfad50fe71da31291b5c43b26c47a
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898903"
---
# <a name="vsct-compiler-command-line-flags"></a>Marcas de la línea de comandos del compilador de VSCT
El Visual Studio de tabla de comandos (VSCT) proporciona modificadores de línea de comandos para garantizar una compilación correcta de los archivos .vsct.

## <a name="command-line-parameters"></a>Parámetros de la línea de comandos
 Para ver la ayuda básica de VSCT desde una ventana Comandos, vaya a la carpeta [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]  \VisualStudioIntegration\Tools\Bin\ de la ruta de instalación del SDK de *Visual Studio* y escriba:

```
vsct /?
```

 Esto devuelve:

```
Microsoft (R) Visual Studio (R) Command Table Compiler Version 3.00.2000

Syntax: vsct <infile> [<outfile>] [-S[symbols file]] [-D<preprocessor-define>]*
[-I<include-path>]* [-L<language>] [-E[C|H|N]:<name>]

  -D    Specify any additional preprocessor defines
  -I    Indicate what additional include paths to send to the preprocessor
  -L    Specify the language to use when selecting strings
  -E    Emit C# objects in the specified namespace for command items,
        followed by [L|F|H|N]:<value>
        F = Name of the file to emit (used if -EL is provided)
        L = Name of a language providing a CodeDOM provider
        N = namespace (required if -EL is provided)
        H = C++ header
  -c    Clean build skipping dependency checks
  -v    Verbose output
```

> [!NOTE]
> Los caracteres ( guion) y / (barra diagonal) se aceptan en notación para indicar parámetros de línea de comandos.

 Las marcas aceptables y lo que significan son las siguientes.

|Switch|Descripción|
|------------|-----------------|
|-d|Especifique los símbolos definidos adicionales.|
|-I|Indique las rutas de acceso de include adicionales que se deben usar al resolver referencias de archivo.|
|-l|Especifique el <xref:System.Globalization.CultureInfo> nombre de la referencia cultural, por ejemplo "en-US".|
|-E|Emita objetos de C# en el espacio de nombres especificado para los elementos de comando, seguido de [C&#124;H&#124;N]:*nombre* de archivo donde C = C#, H = encabezado de C++, N = espacio de nombres. El espacio de nombres es necesario para C#.|
|-v|Salida detallada.|

 El modificador -L indica al compilador que seleccione un grupo de cadenas para generar el archivo .cto binario correspondiente al nombre de referencia <xref:System.Globalization.CultureInfo> cultural especificado. El nombre de referencia cultural especificado debe coincidir con el atributo Language de uno o varios [elementos Strings](../../extensibility/strings-element.md) del archivo .vsct. Si un elemento Strings no tiene ningún atributo Language, se hereda del elemento [CommandTable que lo contiene.](../../extensibility/commandtable-element.md)

 Un archivo .vsct puede tener varios elementos Strings y cada uno puede tener un atributo Language diferente. La globalización se logra ejecutando el compilador vsct varias veces y cambiando el modificador -L para cada nombre de referencia cultural.

 Si el nombre de referencia cultural especificado por el modificador -L no coincide con el atributo Language de ningún elemento Strings, el compilador intentará coincidir con el idioma y no con la región. Por ejemplo, si no se encuentra "en-US", el compilador probará "en" en su lugar. Si no lo hace, probará la referencia cultural actual del sistema operativo. Si no lo hace, compilará el primer elemento Strings que encuentre.

 El modificador -E se puede usar para emitir un archivo de encabezado de estilo C que contiene los símbolos utilizados por la tabla de comandos, o para emitir un archivo de C# que contiene objetos para los símbolos de comando.

 Los modificadores -D e -I tienen la sintaxis de Cl.exe marcas de preprocesador de C que tienen el mismo nombre. Las definiciones -D que tienen el formato X=Y se usan para la expansión de pruebas basadas en XML \<Defined> en `Condition` atributos. -I include paths are used to resolve , and file references( -I include paths are used to resolve \<Include> , \<Extern> and file \<Bitmap> references. Para obtener más información, vea la Referencia [de esquema XML de VSCT](../../extensibility/vsct-xml-schema-reference.md).

 El compilador de VSCT también puede descompilar un archivo binario creado previamente. Para ello, proporcione un archivo binario para \<infile> .   Si el compilador de VSCT ha generado el archivo binario, tendrá sus símbolos ya incrustados y producirá una salida con los nombres simbólicos en una sección \<Symbols> de la salida. Si el compilador de CTC produjo el binario, la salida contendrá los GUID e ID reales. Si el archivo *.ctsym generado por las versiones actuales de Ctc.exe se encuentra en la misma carpeta que el archivo de entrada binario, los símbolos se cargarán desde ese archivo y se usarán para la salida.

## <a name="see-also"></a>Consulta también
- [Archivos de tabla de comandos de Visual Studio (.Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Referencia del esquema XML de VSCT](../../extensibility/vsct-xml-schema-reference.md)
- [Cómo VSPackages agrega elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
