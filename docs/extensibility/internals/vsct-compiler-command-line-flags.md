---
title: Indicadores de línea de comandos del compilador de VSCT ? Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703966"
---
# <a name="vsct-compiler-command-line-flags"></a>Marcas de la línea de comandos del compilador de VSCT
El compilador de la tabla de comandos de Visual Studio (VSCT) proporciona modificadores de línea de comandos para garantizar la compilación correcta de archivos .vsct.

## <a name="command-line-parameters"></a>Parámetros de línea de comandos
 Para ver la ayuda [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] básica de VSCT desde una ventana **de comandos,** desplácese hasta la carpeta y el tipo de la ruta de instalación del SDK de *Visual Studio:*

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
> Los caracteres - (dash) y / (barra diagonal) son notación aceptada para indicar parámetros de línea de comandos.

 Las banderas aceptables y lo que quieren decir son las siguientes.

|Switch|Descripción|
|------------|-----------------|
|-d|Especifique los símbolos definidos adicionales.|
|-I|Indique las rutas de acceso de inclusión adicionales que se deben utilizar al resolver referencias de archivo.|
|-l|Especifique <xref:System.Globalization.CultureInfo> el nombre de la referencia cultural, por ejemplo "en-US".|
|-E|Emita objetos de C- en el espacio de nombres especificado para los elementos de comando, seguido de [C&#124;H&#124;N]: nombre de*archivo*en el que se encuentra el encabezado de C- C, H, C++, N . El espacio de nombres es necesario para C.|
|-v|Salida detallada.|

 El modificador -L indica al compilador que seleccione un grupo de cadenas para generar <xref:System.Globalization.CultureInfo> el archivo binario .cto que corresponde al nombre de referencia cultural especificado. El nombre de referencia cultural especificado debe coincidir con el atributo Language de uno o varios [elementos Strings](../../extensibility/strings-element.md) del archivo .vsct. Si un elemento Strings no tiene ningún atributo Language, se hereda del [elemento CommandTable que](../../extensibility/commandtable-element.md)lo contiene.

 Un archivo .vsct puede tener varios elementos Strings y cada uno puede tener un atributo Language diferente. La globalización se logra ejecutando el compilador VSCT varias veces y cambiando el modificador -L para cada nombre de referencia cultural.

 Si el nombre de referencia cultural especificado por el modificador -L no coincide con el atributo Language de ningún elemento Strings, el compilador intentará que coincida con el idioma y no con la región. Por ejemplo, si no se puede encontrar "en-US", el compilador intentará "en" en su lugar. En caso contrario, intentará la referencia cultural actual del sistema operativo. En caso contrario, compilará el primer elemento Strings que encuentre.

 El modificador -E se puede utilizar para emitir un archivo de encabezado de estilo C que contiene los símbolos que utiliza la tabla de comandos, o para emitir un archivo de C- que contiene objetos para los símbolos de comando.

 Los modificadores -D y -I tienen la sintaxis de los indicadores de preprocesador Cl.exe C que tienen el mismo nombre. -D las definiciones que tienen el formato X-Y \<se utilizan `Condition` para la expansión de las pruebas definidas> basadas en XML en atributos. -Incluir rutas de acceso \<se \<utilizan para \<resolver las referencias de archivo Include>, Extern> y Bitmap>. Para obtener más información, vea referencia de [esquema XML de VSCT](../../extensibility/vsct-xml-schema-reference.md).

 El compilador VSCT también puede descompilar un archivo binario compilado anteriormente. Para ello, proporcione un archivo \<binario para el> infile.   Si el archivo binario fue producido por el compilador VSCT, tendrá sus símbolos ya \<incrustados y producirá la salida con los nombres simbólicos en un símbolos> sección de la salida. Si el binario fue producido por el compilador CTC, la salida contendrá los GUID y los GUID reales. Si el archivo *.ctsym generado por las versiones actuales de Ctc.exe está en la misma carpeta que el archivo de entrada binario, los símbolos se cargarán desde ese archivo y se utilizarán para la salida.

## <a name="see-also"></a>Vea también
- [Archivos de tabla de comandos de Visual Studio (.Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Referencia del esquema XML de VSCT](../../extensibility/vsct-xml-schema-reference.md)
- [Cómo VSPackages agrega elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
