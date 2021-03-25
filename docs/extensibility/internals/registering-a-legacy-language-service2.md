---
title: Registrando un service2 de lenguaje heredado | Microsoft Docs
description: En este artículo se enumeran las entradas del registro para las diversas opciones de servicio de lenguaje disponibles en Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, language services
- language services, registry information
- registry, language services
ms.assetid: ca312aa3-f9f1-4572-8553-89bf3a724deb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fbad469b28c0b8a6aab070d47cf12c326beb92d8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062790"
---
# <a name="registering-a-legacy-language-service-2"></a>Registro de un servicio de lenguaje heredado 2
En las secciones siguientes se proporcionan listas de entradas del registro para las distintas opciones de servicio de lenguaje disponibles en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

 En la siguiente lista de entradas del registro, *vs reg root* es igual a HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\ *X. y*, donde *x. y* es el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] número de versión.

## <a name="registry-entries-for-language-service-options"></a>Entradas del registro para las opciones del servicio de lenguaje
 La clave del nombre de idioma de \Languages\Language Services *raíz de vs reg* \\  puede contener los valores siguientes.

|Nombre|Tipo|Intervalo|Descripción|
|----------|----------|-----------|-----------------|
|(Es el valor predeterminado).|REG_SZ|*\<GUID>*|GUID del servicio de lenguaje.|
|LangResID|REG_DWORD|0X0-0xFFFF|Identificador de recursos de cadena (ResID) para el nombre de texto localizado del idioma.|
|Paquete|REG_SZ|*\<GUID>*|GUID del VSPackage.|
|ShowCompletion|REG_DWORD|0-1|Especifica si las opciones de **finalización de instrucciones** del cuadro de diálogo **Opciones** están habilitadas.|
|ShowSmartIndent|REG_DWORD|0-1|Especifica si está habilitada la opción para seleccionar sangría **inteligente** en el cuadro de diálogo **Opciones** .|
|RequestStockColors|REG_DWORD|0-1|Especifica si los colores predeterminados o personalizados se utilizan para colorear palabras clave.|
|ShowHotURLs|REG_DWORD|0-1|Especifica si el usuario puede hacer clic en las direcciones URL.|
|De forma predeterminada a direcciones URL no activas|REG_DWORD|0-1|Especifica el valor inicial de la opción **Habilitar navegación de direcciones URL con un solo clic** en el cuadro de diálogo **Opciones** .|
|DefaultToInsertSpaces|REG_DWORD|0-1|Especifica si el servicio de lenguaje tiene "Insertar espacios" como opción de la pestaña predeterminada.|
|ShowDropdownBarOption|REG_DWORD|0-1|Habilita o deshabilita la opción **barra de navegación** del cuadro de diálogo **Opciones** que muestra u oculta la **barra de navegación**.|
|Solo ventana de código único|REG_DWORD|0-1|Habilita o deshabilita la **nueva** opción de ventana en el menú **ventana** para un servicio de lenguaje.|
|EnableAdvancedMembersOption|REG_DWORD|0-1|Habilita o deshabilita un valor del cuadro de diálogo **Opciones** para **ocultar los miembros avanzados**.|
|Compatibilidad CF_HTML|REG_DWORD|0-1|Especifica si el editor permite copiar y pegar datos HTML.|
|EnableLineNumbersOption|REG_DWORD|0-1|Especifica si las opciones de los **números de línea** del cuadro de diálogo **Opciones** están habilitadas para un servicio de lenguaje.|
|HideAdvancedMembersByDefault|REG_DWORD|0-1|Especifica si los miembros avanzados como los campos privados están ocultos en las listas de finalización.|
|ShowBraceCompletion|REG_DWORD|0-1|Especifica si está habilitada la opción de **finalización de llave** en el cuadro de diálogo **Opciones** .|

### <a name="example"></a>Ejemplo

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    Language Services\
      C/C++\
        (Default)             = reg_sz:{B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}
        LangResID             = reg_dword:0x00000000
        Package               = reg_sz:{8C2EA640-ABC1-11D0-9D62-00C04FD9DFD9}
        ShowCompletion        = reg_dword:0x00000001
        ShowSmartIndent       = reg_dword:0x00000001
        ShowDropdownBarOption = reg_dword:0x00000001
```

## <a name="registry-entries-for-debugger-languages-options"></a>Entradas del registro para las opciones de idiomas del depurador
 La clave de *vs reg root*\Languages\Language Services \\ *Name*\Debugger Languages \\ *GUID*\ Key puede incluir los valores siguientes.

|Nombre|Tipo|Intervalo|Descripción|
|----------|----------|-----------|-----------------|
|(Es el valor predeterminado).|REG_SZ|text|El valor predeterminado se puede usar para documentar el nombre del idioma. El nombre de esta clave es un GUID de un evaluador de expresiones que tiene una entrada correspondiente en el *\<VS Reg Root>* evaluador de \AD7Metrics\Expression.|

### <a name="example"></a>Ejemplo

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    Language Services\
      C/C++\
        Debugger Languages\
          {3A12D0B7-C26C-11D0-B442-00A0244A1DD2}\
            (Default) = reg_sz:C++
```

## <a name="registry-entries-for-editor-tools-options"></a>Entradas del registro para las opciones de herramientas del editor
 Puede agregar claves del registro en la clave EditorToolsOptions para las páginas de propiedades y los nodos de propiedad. Estas claves y sus valores identifican las páginas de propiedades en el cuadro de diálogo **Opciones** (en el menú **herramientas** ) que se usan para configurar el servicio de lenguaje. En el ejemplo siguiente, el nombre de la *Página* es el nombre de una página de propiedades y el *nombre del nodo* es el nombre de un nodo en el árbol del cuadro de diálogo **Opciones** . La entrada de la página y la entrada del nodo deben especificarse por separado.

|Nombre|Tipo|Intervalo|Descripción|
|----------|----------|-----------|-----------------|
|(Es el valor predeterminado).|REG_SZ|ResID|El nombre para mostrar localizado de esta página de opciones. El nombre puede ser texto literal, o # `nnn` , donde `nnn` es un identificador de recurso de cadena en el archivo dll satélite del VSPackage especificado.|
|Paquete|REG_SZ|*GUID*|GUID del VSPackage que implementa esta página de opciones.|
|Página|REG_SZ|*GUID*|GUID de la página de propiedades que se va a solicitar del VSPackage mediante una llamada al <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> método. Si esta entrada del registro no está presente, la clave del registro describe un nodo, no una página.|

### <a name="example"></a>Ejemplo

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    Language Services\
      CSharp\
        EditorToolsOptions\
          Formatting\
            (Default) = reg_sz:#242
            Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}
            General\
              (Default) = reg_sz:#255
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}
              Page      = reg_sz:{3EB2CC0B-033E-4D75-B26A-B2362C25227E}
            Indentation\
              (Default) = reg_sz:#250
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}
              Page      = reg_sz:{5E21D017-6D2A-4114-A1F1-C923F001CBBB}
            Newlines\
              (Default) = reg_sz:#253
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}
              Page      = reg_sz:{607D8062-68D1-41E4-9A35-B5E7F14D0481}
```

## <a name="registry-entries-for-file-name-extension-options"></a>Entradas del registro para las opciones de extensión de nombre de archivo
 La entrada de la extensión de archivo debe incluir el punto inicial, por ejemplo ". myext".

|Nombre|Tipo|Intervalo|Descripción|
|----------|----------|-----------|-----------------|
|(Es el valor predeterminado).|REG_SZ|*GUID*|GUID de servicio del servicio de lenguaje predeterminado para este tipo de extensión de nombre de archivo.|

### <a name="example"></a>Ejemplo

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    File Extensions\
      .cpp\
        (Default) = {B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}
```

## <a name="registry-entries-for-editor-options"></a>Entradas del registro para las opciones del editor
 La clave \Editors de *vs reg raíz* puede contener los siguientes valores:

|Nombre|Tipo|Intervalo|Descripción|
|----------|----------|-----------|-----------------|
|(Es el valor predeterminado).|REG_SZ|""|Sin usar puede poner su nombre aquí para la documentación.|
|DefaultToolboxTab|REG_SZ|""|Nombre de la pestaña del cuadro de herramientas que se va a establecer como predeterminada cuando el editor está activo.|
|DisplayName|REG_SZ|ResID|Nombre que se va a mostrar en el cuadro de diálogo **abrir con** . El nombre es el identificador de recurso de cadena o un nombre en formato estándar.|
|ExcludeDefTextEditor|REG_DWORD|0-1|Se usa para el comando de menú **abrir con** . Si no desea mostrar el editor de texto predeterminado en la lista de editores disponibles para un tipo de archivo específico, establezca este valor en 1.|
|LinkedEditorGUID|REG_SZ|*\<GUID>*|Se usa para cualquier servicio de lenguaje que pueda abrir un archivo con compatibilidad con la página de códigos. Por ejemplo, al abrir un archivo. txt con el comando **abrir con** , se proporcionan opciones para usar el editor de código fuente con y sin codificación.<br /><br /> El GUID especificado en el nombre de la subclave es para el generador de editores de página de códigos; el GUID vinculado especificado en esta entrada de registro específica es para el generador de editores normal. La finalidad de esta entrada es que si el IDE no abre un archivo con el editor predeterminado, el IDE intentará usar el siguiente editor de la lista. El siguiente editor no debe ser el generador de editores de página de códigos porque este generador de editores es básicamente el mismo que el generador de editores en el que se produjo el error.|
|Paquete|REG_SZ|*\<GUID>*|GUID de VSPackage del ResID del nombre para mostrar.|

### <a name="example"></a>Ejemplo

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  \Editors\
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\
      (Default)            = reg_sz:Html Editor with Encoding
      DefaultToolboxTab    = reg_sz:HTML
      DisplayName          = reg_sz:#20101
      LinkedEditorGUID     = reg_sz:{C76D83F8-A489-11D0-8195-00A0C91BBEE3}
      Package              = reg_sz:{1B437D20-F8FE-11D2-A6AE-00104BCC7269}
```

## <a name="registry-entries-for-logical-view-options"></a>Entradas del registro para opciones de vista lógica
 La \Editors de interfaz de>usuario de *vs reg root* \\ *Editor* puede contener los siguientes valores.

|Nombre|Tipo|Intervalo|Descripción|
|----------|----------|-----------|-----------------|
|(Es el valor predeterminado).|REG_SZ||Sin usar.|
|*\<GUID>*|REG_SZ|""|Clave para las vistas lógicas admitidas. Puede tener tantos como necesite. El nombre de la entrada del registro es lo que es importante, no el valor, que siempre es una cadena vacía.|

### <a name="example"></a>Ejemplo

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  \Editors\
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\
      LogicalViews\
       (Default) = reg_sz:
       {7651a700-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:
       {7651a701-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:
       {7651a702-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:
       {7651a703-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:
```

## <a name="registry-entries-for-editor-extension-options"></a>Entradas del registro para las opciones de extensión del editor
 La clave \Extensions del GUID del editor \Editors de *vs reg* \\ puede contener los valores siguientes. La extensión de nombre de archivo no incluye el punto inicial.

|Nombre|Tipo|Intervalo|Descripción|
|----------|----------|-----------|-----------------|
|(Es el valor predeterminado).|REG_SZ||Sin usar.|
|*\<ext>*|REG_DWORD|0-0xFFFFFFFF|Prioridad relativa de las extensiones. Si dos o más idiomas comparten la misma extensión, se elige el idioma de mayor prioridad.|

 Además, la selección predeterminada del usuario actual para un editor se almacena en HKEY_Current_User \Software\Microsoft\VisualStudio \\ *X. Y*\Default Editors \\ *ext*. El GUID del servicio de lenguaje seleccionado está en la entrada personalizada. Esto tiene prioridad para el usuario actual.

### <a name="example"></a>Ejemplo

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\
  \Editors\
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\
      Extensions\
       (Default) = reg_sz:
       *         = reg_dword:0x00000018
       html      = reg_dword:0x00000027
       shtm      = reg_dword:0x00000027
       shtml     = reg_dword:0x00000027
```

## <a name="registry-entries-for-managed-package-framework-language-service-options"></a>Entradas del registro para las opciones del servicio de lenguaje de Managed Package Framework
 Las siguientes entradas del registro son específicas de las clases de servicio de lenguaje de Managed Package Framework (MPF). Estas entradas del registro indican la compatibilidad en el servicio de lenguaje para varias características de IntelliSense y otras características de edición avanzadas.

 Se tiene acceso a estas entradas del registro a través de la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> clase.

|Nombre|Tipo|Intervalo|Descripción|
|----------|----------|-----------|-----------------|
|CodeSense|REG_DWORD|0-1|Compatibilidad con las operaciones de IntelliSense.|
|MatchBraces|REG_DWORD|0-1|Compatibilidad con pares de idiomas coincidentes, como llaves, paréntesis y corchetes.|
|InformaciónRápida|REG_DWORD|0-1|Compatibilidad con la operación de información rápida de IntelliSense.|
|ShowMatchingBrace|REG_DWORD|0-1|Compatibilidad para mostrar el par de idiomas coincidentes en la barra de estado.|
|MatchBracesAtCaret|REG_DWORD|0-1|Compatibilidad para mostrar pares de idiomas coincidentes, normalmente mediante el resaltado de los dos elementos.|
|MaxErrorMessages|REG_DWORD|0-n|Número máximo de errores que se pueden mostrar en la ventana de **lista de errores** .|
|CodeSenseDelay|REG_DWORD|0-n|Número de milisegundos de retraso antes de iniciar cualquier análisis en segundo plano para una operación de IntelliSense.|
|EnableAsyncCompletion|REG_DWORD|0-1|Compatibilidad con el análisis en segundo plano.|
|EnableCommenting|REG_DWORD|0-1|Compatibilidad para marcar como comentario los bloques de texto seleccionados y también implica compatibilidad para quitar los comentarios del texto seleccionado.|
|EnableFormatSelection|REG_DWORD|0-1|Compatibilidad con el formato de texto como la sangría automática o el ajuste de la posición de las llaves.|
|AutoOutlining|REG_DWORD|0-1|Compatibilidad con la esquematización (regiones que se pueden contraer).|
|MaxRegions|REG_DWORD|0-n|Número máximo de regiones ocultas por archivo.|

```
ExampleHKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    Language Services\
      XML\
        (Default)             = reg_sz:{f6819a78-a205-47b5-be1c-675b3c7f0b8e}
        MatchBraces           = reg_dword:0x00000001
        QuickInfo             = reg_dword:0x00000001
        ShowMatchingBrace     = reg_dword:0x00000001
        MatchBracesAtCaret    = reg_dword:0x00000000
        MaxErrorMessages      = reg_dword:0x00000064
        CodeSenseDelay        = reg_dword:0x000001f4
        MaxRegions            = reg_dword:0x0000000a
```

## <a name="see-also"></a>Consulte también
- [Desarrollo de un servicio de lenguaje heredado](../../extensibility/internals/developing-a-legacy-language-service.md)
