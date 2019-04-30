---
title: Marcadores de línea de comandos del compilador VSCT | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, compiling
- command-table file compilation (VSCT files)
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe73a4d66d57ae362d4b99d10aca9170971f17b9
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63429634"
---
# <a name="vsct-compiler-command-line-flags"></a>Marcas de la línea de comandos del compilador de VSCT
El compilador de la tabla de comandos de Visual Studio (VSCT) proporciona modificadores de línea de comandos para asegurarse de la compilación correcta de los archivos .vsct.

## <a name="command-line-parameters"></a>Parámetros de línea de comandos
 Para ver la Ayuda VSCT básica de un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **comando** ventana, desplácese hasta la *ruta de instalación del SDK de Visual Studio*\VisualStudioIntegration\Tools\Bin\ carpeta y escriba:

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
> Los caracteres - (dash) y / (barra diagonal) son ambos aceptados notación para indicar los parámetros de línea de comandos.

 Marcas aceptables y su significado son los siguientes.

|Modificador|Descripción|
|------------|-----------------|
|-D|Especifique todos los símbolos definidos adicionales.|
|-I|Indicar que el adicional incluir rutas de acceso que se deben usar al resolver referencias de archivo.|
|-L|Especifique el <xref:System.Globalization.CultureInfo> nombre de referencia cultural, por ejemplo "en-US".|
|-E|Emitir C# objetos en el espacio de nombres especificado para los elementos de comando, seguido por [C&#124;H&#124;N]:*filename*donde C = C#, H = C++ encabezado, N = el espacio de nombres. El espacio de nombres es necesaria para C#.|
|-v|Salida detallada.|

 El modificador -L indica al compilador que seleccione un grupo de cadenas para generar el archivo .cto binario que se corresponde con el dado <xref:System.Globalization.CultureInfo> nombre de referencia cultural. El nombre de la referencia cultural especificada debe coincidir con el atributo de idioma de uno o varios [Strings (elemento)](../../extensibility/strings-element.md) en el archivo .vsct. Si un elemento de cadenas no tiene ningún atributo de idioma, se hereda de la que contiene [CommandTable (elemento)](../../extensibility/commandtable-element.md).

 Un archivo .vsct puede tener varios elementos de cadenas, y cada uno puede tener un atributo de idioma diferente. Globalización se logra al ejecutar el compilador VSCT varias veces y cambiar el conmutador -L para cada nombre de referencia cultural.

 Si el nombre de la referencia cultural proporcionado por el conmutador -L no coincide con el atributo de idioma de cualquier elemento de cadenas, el compilador intentará coincidir con el lenguaje y no la región. Por ejemplo, si no se encuentra "en-US", el compilador intentará "en" en su lugar. En caso contrario, tratará de la referencia cultural actual del sistema operativo. En caso contrario, se compilará el primer elemento de cadenas que se encuentra.

 El interruptor -E puede usarse para emitir un archivo de encabezado de estilo C que contiene los símbolos utilizados por la tabla de comandos, o para emitir un archivo de C# que contiene los objetos de los símbolos de comando.

 -D y - conmutadores tienen la sintaxis de las marcas de preprocesador de Cl.exe C que tienen el mismo nombre. -D definiciones que tienen el formato X = Y se usan para la expansión de basado en XML \<Defined > pruebas en `Condition` atributos. -I incluir rutas de acceso se utilizan para resolver \<Include >, \<Extern > y \<mapa de bits > las referencias de archivo. Para obtener más información, consulte el [VSCT XML Schema Reference](../../extensibility/vsct-xml-schema-reference.md).

 El compilador VSCT también puede descompilar un archivo binario compilado anteriormente. Para ello, proporcione un archivo binario para la \<infile >.   Si el archivo binario se ha generado por el compilador VSCT, tendrán sus símbolos ya incrustados y genera una salida con los nombres simbólicos en una \<símbolos > sección de la salida. Si el binario ha generado por el compilador CTC, la salida contendrá los GUID e identificadores reales. Si el archivo *.ctsym producidos por las versiones actuales de Ctc.exe está en la misma carpeta que el archivo binario de entrada, los símbolos se cargarán desde ese archivo y se usa para la salida.

## <a name="see-also"></a>Vea también
- [Archivos de tabla de comandos de Visual Studio (.Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Referencia del esquema XML de VSCT](../../extensibility/vsct-xml-schema-reference.md)
- [Adición de elementos de la interfaz de usuario por VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)