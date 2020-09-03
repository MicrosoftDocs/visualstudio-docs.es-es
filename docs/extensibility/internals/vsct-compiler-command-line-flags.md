---
title: Marcas de la línea de comandos del compilador VSCT | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, compiling
- command-table file compilation (VSCT files)
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e4ee29710049453c3163c366eccf96e257b6028d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80703966"
---
# <a name="vsct-compiler-command-line-flags"></a>Marcas de la línea de comandos del compilador de VSCT
El compilador de la tabla de comandos de Visual Studio (VSCT) proporciona modificadores de línea de comandos para garantizar la correcta compilación de los archivos. VSCT.

## <a name="command-line-parameters"></a>Parámetros de la línea de comandos
 Para ver la ayuda de VSCT básica desde una ventana de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **comandos** , vaya a la carpeta *ruta de instalación de Visual Studio SDK*\VisualStudioIntegration\Tools\Bin\ y escriba:

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
> Los caracteres (guión) y/(barra diagonal) son la notación aceptada para indicar los parámetros de la línea de comandos.

 Los marcadores aceptables y lo que significan son los siguientes.

|Switch|Descripción|
|------------|-----------------|
|-d|Especifique cualquier símbolo definido adicional.|
|-I|Indicar las rutas de acceso de inclusión adicionales que se deben usar al resolver las referencias de archivo.|
|-l|Especifique el <xref:System.Globalization.CultureInfo> nombre de la referencia cultural, por ejemplo "en-US".|
|-E|Emitir objetos de C# en el espacio de nombres especificado para los elementos de comando, seguidos de [C&#124;H&#124;N]:*nombre de archivo*donde C = C#, H = encabezado de C++, N = espacio de nombres. El espacio de nombres es necesario para C#.|
|-v|Salida detallada.|

 El modificador-L indica al compilador que seleccione un grupo de cadenas para generar el archivo binario. CTO correspondiente al <xref:System.Globalization.CultureInfo> nombre de la referencia cultural especificada. El nombre de referencia cultural especificado debe coincidir con el atributo Language de uno o más [elementos Strings](../../extensibility/strings-element.md) del archivo. Vsct. Si un elemento Strings no tiene ningún atributo Language, se hereda del [elemento CommandTable](../../extensibility/commandtable-element.md)que lo contiene.

 Un archivo. Vsct puede tener varios elementos de cadena y cada uno de ellos puede tener un atributo de idioma diferente. La globalización se consigue al ejecutar el compilador VSCT varias veces y cambiar el modificador-L para cada nombre de referencia cultural.

 Si el nombre de la referencia cultural proporcionado por el modificador-L no coincide con el atributo Language de ningún elemento Strings, el compilador intentará coincidir con el idioma y no con la región. Por ejemplo, si no se encuentra "en-US", el compilador probará "en" en su lugar. Si no es así, probará la referencia cultural actual del sistema operativo. Si no es así, se compilará el primer elemento de cadenas que encuentre.

 El modificador-E se puede usar para emitir un archivo de encabezado de estilo C que contiene los símbolos que se usan en la tabla de comandos, o para emitir un archivo de C# que contiene objetos para los símbolos de comando.

 Los modificadores-D e-I tienen la sintaxis de las marcas de preprocesador de Cl.exe C que tienen el mismo nombre. Las definiciones de-D que tienen el formato X = Y se usan para la expansión de \<Defined> pruebas basadas en XML en `Condition` atributos. -I incluye las rutas de acceso que se usan para resolver \<Include> \<Extern> \<Bitmap> las referencias de archivo y. Para obtener más información, vea la [Referencia del esquema XML de VSCT](../../extensibility/vsct-xml-schema-reference.md).

 El compilador VSCT también puede descompilar un archivo binario compilado previamente. Para ello, proporcione un archivo binario para \<infile> .   Si el compilador VSCT generó el archivo binario, tendrá sus símbolos ya incrustados y generará una salida con los nombres simbólicos en una \<Symbols> sección de la salida. Si el binario fue generado por el compilador de CTC, el resultado contendrá los identificadores y GUID reales. Si el archivo *. ctsym generado por las versiones actuales de Ctc.exe está en la misma carpeta que el archivo de entrada binaria, los símbolos se cargarán desde ese archivo y se usarán para la salida.

## <a name="see-also"></a>Consulte también
- [Archivos de tabla de comandos de Visual Studio (.Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Referencia del esquema XML de VSCT](../../extensibility/vsct-xml-schema-reference.md)
- [Cómo VSPackages agrega elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
