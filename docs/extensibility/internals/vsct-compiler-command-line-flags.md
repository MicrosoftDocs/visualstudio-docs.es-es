---
title: Marcadores de línea de comandos del compilador VSCT | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, compiling
- command-table file compilation (VSCT files)
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6e2e1045adb451c7f4dd06b888fca356d26b7ff3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="vsct-compiler-command-line-flags"></a>Marcadores de línea de comandos del compilador VSCT
El compilador de la tabla de comandos de Visual Studio (VSCT) proporciona modificadores de línea de comandos para asegurarse de compilación correcta de los archivos de vsct.  
  
## <a name="command-line-parameters"></a>Parámetros de línea de comandos  
 Para ver la Ayuda VSCT básica de un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **comando** ventana, vaya a la *ruta de instalación del SDK de Visual Studio*\VisualStudioIntegration\Tools\Bin\ carpeta y escriba:  
  
```  
vsct /?  
```  
  
 Esto devuelve:  
  
```  
Microsoft (R) Visual Studio (R) Command Table Compiler Version 3.00.2000  
  
Syntax: vsct <infile> [<outfile>] [-S[symbols file]] [-D<preprocessor-define>]*  
[-I<include-path>]* [-L<language>] [-E[C|H|N]:<name>]  
  
  -D    Specify any additional preprocessor defines  
  -I    Indcate what additional include paths to send to the preprocessor  
  -L    Specify the langauge to use when selecting strings  
  -E    Emit C# objects in the specified namespace for command items,  
        folowed by [L|F|H|N]:<value>  
        F = Name of the file to emit (used if -EL is provided)  
        L = Name of a language providing a CodeDOM provider  
        N = namespace (required if -EL is provided)  
        H = C++ header  
  -c    Clean build skipping dependancy checks  
  -v    Verbose output  
```  
  
> [!NOTE]
>  Los caracteres - (guión) y / (barra diagonal) son ambos aceptado notación para indicar los parámetros de línea de comandos.  
  
 Marcas aceptables y lo que significan son los siguientes.  
  
|Modificador|Descripción|  
|------------|-----------------|  
|-D|Especifique todos los símbolos definidos adicionales.|  
|-I|Indicar que el adicionales incluyen rutas de acceso que se deben usar al resolver referencias de archivo.|  
|-L|Especifique el <xref:System.Globalization.CultureInfo> nombre de referencia cultural, por ejemplo "en-US".|  
|-E|Emitir objetos de C# en el espacio de nombres especificado para los elementos de comando, seguido por [C&#124;H&#124;N]:*filename*donde C = C#, H = encabezado de C++, N = espacio de nombres. El espacio de nombres es necesario en C#.|  
|-v|Resultado detallado.|  
  
 El modificador -L indica al compilador que seleccione un grupo de cadenas para generar el archivo .cto binario que se corresponde con el determinado <xref:System.Globalization.CultureInfo> nombre de referencia cultural. El nombre de la referencia cultural especificada debe coincidir con el atributo de idioma de uno o varios [cadenas elemento](../../extensibility/strings-element.md) en el archivo .vsct. Si un elemento de cadenas no tiene ningún atributo de idioma, se hereda de la que contiene [CommandTable elemento](../../extensibility/commandtable-element.md).  
  
 Un archivo .vsct puede tener varios elementos de cadenas, y cada uno puede tener un atributo de idioma diferente. Globalización se logra al ejecutar el compilador VSCT varias veces y cambiar el conmutador -L para cada nombre de referencia cultural.  
  
 Si el nombre de referencia cultural especificado por el modificador -L no coincide con el atributo de idioma de cualquier elemento de cadenas, el compilador intentará coincidir con el idioma y no la región. Por ejemplo, si no se encuentra "en-US", el compilador intentará "es-es" en su lugar. En su defecto, intentará la referencia cultural actual del sistema operativo. En su defecto, se compilará el primer elemento de cadenas que se encuentra.  
  
 El modificador -E puede usarse para emitir un archivo de encabezado de estilo C que contiene los símbolos utilizados por la tabla de comandos, o para emitir un archivo C# que contiene objetos para los símbolos de comando.  
  
 -D e - I conmutadores tienen la sintaxis de las marcas de preprocesador de Cl.exe C que tienen el mismo nombre. -D las definiciones que tienen el formato X = Y se utilizan para la expansión de XML-based \<Defined > pruebas en `Condition` atributos. -Se incluyen las rutas de acceso se utilizan para resolver \<Include >, \<Extern > y \<mapa de bits > referencias de archivo. Para obtener más información, consulte el [referencia de esquemas XML de VSCT](../../extensibility/vsct-xml-schema-reference.md).  
  
 El compilador VSCT también puede descompilar un archivo binario generado anteriormente. Para ello, proporcione un archivo binario para el \<infile >.   Si el archivo binario se ha generado por el compilador VSCT, tendrán sus símbolos ya insertados y generará un resultado con los nombres simbólicos en una \<símbolos > sección de la salida. Si el archivo binario se ha generado por el compilador CTC, la salida contendrá los GUID e identificadores real. Si el archivo *.ctsym generado por las versiones actuales de Ctc.exe está en la misma carpeta que el archivo de entrada binario, los símbolos se cargarán desde ese archivo y se usa para la salida.  
  
## <a name="see-also"></a>Vea también  
 [Tabla de comandos de Visual Studio (. Archivos Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Referencia del esquema XML de VSCT](../../extensibility/vsct-xml-schema-reference.md)   
 [Adición de elementos de la interfaz de usuario por VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)