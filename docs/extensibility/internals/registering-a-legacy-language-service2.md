---
title: Registro de un servicio de lenguaje heredado2 Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, language services
- language services, registry information
- registry, language services
ms.assetid: ca312aa3-f9f1-4572-8553-89bf3a724deb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d9d13f301f6c04c0f7b14cc8c685f08b072ef84
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705886"
---
# <a name="registering-a-legacy-language-service"></a>Registro de un servicio de lenguaje heredado
En las secciones siguientes se proporcionan listas de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]entradas de registro para las distintas opciones de servicio de lenguaje disponibles en .

 En la siguiente lista de entradas del Registro, raíz de *vs, VS Reg es* igual a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] HKEY_LOCAL_MACHINE, SOFTWARE, Microsoft, VisualStudio\\*X.Y*, donde *X.Y* es el número de versión.

## <a name="registry-entries-for-language-service-options"></a>Entradas del Registro para Opciones de Servicio de Lenguaje
 La clave de nombre de\\*idioma* de VS Reg Root (Raíz de registro de *VS)* puede contener los siguientes valores.

|Nombre|Tipo|Intervalo|Descripción|
|----------|----------|-----------|-----------------|
|(Es el valor predeterminado).|REG_SZ|*\<GUID>*|GUID del servicio de lenguaje.|
|LangResID|REG_DWORD|0x0-0xffff|Identificador de recursos de cadena (ResID) para el nombre de texto localizado del idioma.|
|Paquete|REG_SZ|*\<GUID>*|GUID del VSPackage.|
|ShowCompletion|REG_DWORD|0-1|Especifica si las opciones de finalización de **instrucción** en el cuadro de diálogo **Opciones** están habilitadas.|
|ShowSmartIndent|REG_DWORD|0-1|Especifica si la opción para seleccionar Sangría **inteligente** en el cuadro de diálogo **Opciones** está habilitada.|
|RequestStockColors|REG_DWORD|0-1|Especifica si los colores personalizados o predeterminados se utilizan para colorear palabras clave.|
|ShowHotURLs|REG_DWORD|0-1|Especifica si el usuario puede hacer clic en direcciones URL.|
|Predeterminado en URL no calientes|REG_DWORD|0-1|Especifica la configuración inicial de la opción Habilitar navegación URL con **un solo clic** en el cuadro de diálogo **Opciones.**|
|DefaultToInsertSpaces|REG_DWORD|0-1|Especifica si el servicio de lenguaje tiene "insertar espacios" como su opción de ficha predeterminada.|
|ShowDropdownBarOption|REG_DWORD|0-1|Habilita o deshabilita la opción Barra de **navegación** en el cuadro de diálogo **Opciones** que muestra u oculta la barra **de navegación**.|
|Solo una ventana de código único|REG_DWORD|0-1|Habilita o deshabilita la opción **Nueva ventana** del menú **Ventana** de un servicio de idioma.|
|EnableAdvancedMembersOption|REG_DWORD|0-1|Habilita o deshabilita una configuración de cuadro de diálogo **Opciones** para **Ocultar miembros avanzados**.|
|Soporte CF_HTML|REG_DWORD|0-1|Especifica si el editor permite copiar y pegar datos HTML.|
|EnableLineNumbersOption|REG_DWORD|0-1|Especifica si las opciones **Números** de línea del cuadro de diálogo **Opciones** están habilitadas para un servicio de lenguaje.|
|HideAdvancedMembersByDefault|REG_DWORD|0-1|Especifica si los miembros avanzados, como los campos privados, están ocultos en las listas de finalización.|
|ShowBraceCompletion|REG_DWORD|0-1|Especifica si la opción **Finalización** de llaves en el cuadro de diálogo **Opciones** está habilitada.|

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

## <a name="registry-entries-for-debugger-languages-options"></a>Entradas del Registro para Opciones de Lenguajes del Depurador
 La clave DE LA *raíz de registro*de VS , "Idiomas" y Nombre de\\*idioma*de los servicios de lenguaje de los servicios de lenguaje , el\\*GUID*de los idiomas del depurador, puede incluir los siguientes valores.

|Nombre|Tipo|Intervalo|Descripción|
|----------|----------|-----------|-----------------|
|(Es el valor predeterminado).|REG_SZ|text|El valor predeterminado se puede utilizar para documentar el nombre del idioma. El nombre de esta clave es un GUID de un * \< *evaluador de expresiones que tiene una entrada correspondiente en la raíz de vs reg>.|

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

## <a name="registry-entries-for-editor-tools-options"></a>Entradas del Registro para opciones de herramientas del editor
 Puede agregar claves del Registro en la clave EditorToolsOptions para páginas de propiedades y nodos de propiedades. Estas claves y sus valores identifican las páginas de propiedades en el cuadro de diálogo **Opciones** (en el menú **Herramientas)** que se usan para configurar el servicio de lenguaje. En el ejemplo siguiente, *Nombre* de página es el nombre de una página de propiedades y Nombre de *nodo* es el nombre de un nodo del árbol en el cuadro de diálogo **Opciones.** La entrada de página y la entrada de nodo deben especificarse por separado.

|Nombre|Tipo|Intervalo|Descripción|
|----------|----------|-----------|-----------------|
|(Es el valor predeterminado).|REG_SZ|Resnum|El nombre para mostrar localizado de esta página de opciones. El nombre puede ser texto`nnn`literal, o , donde `nnn` es un identificador de recurso de cadena en el archivo DLL satélite del VSPackage especificado.|
|Paquete|REG_SZ|*GUID*|GUID del VSPackage que implementa esta página de opciones.|
|Página|REG_SZ|*GUID*|El GUID de la página de propiedades para <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> solicitar desde el VSPackage mediante una llamada al método. Si esta entrada del Registro no está presente, la clave del Registro describe un nodo, no una página.|

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

## <a name="registry-entries-for-file-name-extension-options"></a>Entradas de registro para opciones de extensión de nombre de archivo
 La entrada de la extensión de archivo debe incluir el período inicial, por ejemplo ".myext".

|Nombre|Tipo|Intervalo|Descripción|
|----------|----------|-----------|-----------------|
|(Es el valor predeterminado).|REG_SZ|*GUID*|GUID de servicio para el servicio de idioma predeterminado para este tipo de extensión de nombre de archivo.|

### <a name="example"></a>Ejemplo

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    File Extensions\
      .cpp\
        (Default) = {B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}
```

## <a name="registry-entries-for-editor-options"></a>Entradas del Registro para Opciones del Editor
 La clave *raíz de VS Reg*, editores, puede contener los siguientes valores:

|Nombre|Tipo|Intervalo|Descripción|
|----------|----------|-----------|-----------------|
|(Es el valor predeterminado).|REG_SZ|""|Sin usar; puede poner su nombre aquí para la documentación.|
|DefaultToolboxTab|REG_SZ|""|Nombre de la pestaña de la caja de herramientas para que se haga por defecto cuando el editor está activo.|
|DisplayName|REG_SZ|Resnum|Nombre para mostrar en el cuadro de diálogo **Abrir** con. El nombre es el identificador de recurso de cadena o un nombre en formato estándar.|
|ExcludeDefTextEditor|REG_DWORD|0-1|Se utiliza para el comando de menú **Abrir con.** Si no desea enumerar el editor de texto predeterminado en la lista de editores disponibles para un tipo de archivo específico, establezca este valor en 1.|
|LinkedEditorGUID|REG_SZ|*\<GUID>*|Se utiliza para cualquier servicio de lenguaje que pueda abrir un archivo con compatibilidad con la página de códigos. Por ejemplo, al abrir un archivo .txt mediante el comando **Abrir con,** se proporcionan opciones para usar el editor de código fuente con y sin codificación.<br /><br /> El GUID especificado en el nombre de la subclave es para el generador del editor de páginas de códigos; el GUID vinculado especificado en esta entrada de registro específica es para el generador de editornormal. El propósito de esta entrada es que si el IDE no abre un archivo mediante el editor predeterminado, el IDE intentará usar el siguiente editor de la lista. Este siguiente editor no debe ser la fábrica del editor de páginas de códigos porque esta fábrica de editores es básicamente la misma que la fábrica del editor que falló.|
|Paquete|REG_SZ|*\<GUID>*|GUID de VSPackage para el nombre para mostrar ResID.|

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

## <a name="registry-entries-for-logical-view-options"></a>Entradas del Registro para Opciones de Vista Lógica
 La\\*interfaz de usuario *de LA GUI de VS Reg Root (Raíz de registro de *VS)*>la clave .LogicalViews puede contener los siguientes valores.

|Nombre|Tipo|Intervalo|Descripción|
|----------|----------|-----------|-----------------|
|(Es el valor predeterminado).|REG_SZ||Sin usar.|
|*\<GUID>*|REG_SZ|""|Clave de las vistas lógicas admitidas. Puedes tener tantos de estos como necesites. El nombre de la entrada del registro es lo que es importante, no el valor, que siempre es una cadena vacía.|

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

## <a name="registry-entries-for-editor-extension-options"></a>Entradas del Registro para Opciones de Extensión Editor
 La clave GUID de *la raíz de vsregistro*de VS Reg ,\\el*editor*de editores de editores, puede contener los siguientes valores. La extensión de nombre de archivo no incluye el período inicial.

|Nombre|Tipo|Intervalo|Descripción|
|----------|----------|-----------|-----------------|
|(Es el valor predeterminado).|REG_SZ||Sin usar.|
|*\<ext>*|REG_DWORD|0-0xffffffff|Prioridad relativa de las extensiones. Si dos o más idiomas comparten la misma extensión, se elige el idioma de mayor prioridad.|

 Además, la selección predeterminada del usuario actual para un editor se\\almacena en HKEY_Current_User, Software, Microsoft, VisualStudio*X.Y,* Editores\\*predeterminados.* El GUID del servicio de idioma seleccionado se encuentra en la entrada personalizada. Esto tiene prioridad para el usuario actual.

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

## <a name="registry-entries-for-managed-package-framework-language-service-options"></a>Entradas del Registro para opciones de servicio de lenguaje de Managed Package Framework
 Las siguientes entradas del Registro son específicas de las clases de servicio de lenguaje del marco de paquete administrado (MPF). Estas entradas del Registro indican compatibilidad en el servicio de lenguaje para varias características de IntelliSense y para otras características de edición avanzadas.

 Se accede a estas <xref:Microsoft.VisualStudio.Package.LanguagePreferences> entradas del registro a través de la clase.

|Nombre|Tipo|Intervalo|Descripción|
|----------|----------|-----------|-----------------|
|CodeSense|REG_DWORD|0-1|Compatibilidad con operaciones de IntelliSense.|
|MatchBraces|REG_DWORD|0-1|Compatibilidad con pares de idiomas coincidentes, como llaves, paréntesis y corchetes.|
|InformaciónRápida|REG_DWORD|0-1|Compatibilidad con la operación de información rápida de IntelliSense.|
|ShowMatchingBrace|REG_DWORD|0-1|Compatibilidad para mostrar el par de idioma coincidente en la barra de estado.|
|MatchBracesAtCaret|REG_DWORD|0-1|Compatibilidad con la visualización de pares de idiomas coincidentes, normalmente resaltando los dos elementos.|
|MaxErrorMessages|REG_DWORD|0-n|El número máximo de errores que se pueden mostrar en la ventana **Lista** de errores.|
|CodeSenseDelay|REG_DWORD|0-n|El número de milisegundos que se debe retrasar antes de iniciar cualquier análisis en segundo plano para una operación de IntelliSense.|
|EnableAsyncCompletion|REG_DWORD|0-1|Soporte para el análisis en segundo plano.|
|Habilitarcomentarios|REG_DWORD|0-1|Compatibilidad con comentarios de bloques de texto seleccionados, y también implica compatibilidad para quitar los comentarios del texto seleccionado.|
|EnableFormatSelection|REG_DWORD|0-1|Compatibilidad con el formato de texto, como la sangría automática o el ajuste de la posición de las llaves.|
|AutoOutlining|REG_DWORD|0-1|Compatibilidad con esquematización (regiones que se pueden contraer).|
|MaxRegions|REG_DWORD|0-n|El número máximo de regiones ocultas por archivo.|

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

## <a name="see-also"></a>Vea también
- [Desarrollo de un servicio de lenguaje heredado](../../extensibility/internals/developing-a-legacy-language-service.md)
