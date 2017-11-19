---
title: Registrar un Service2 de lenguaje heredado | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, language services
- language services, registry information
- registry, language services
ms.assetid: ca312aa3-f9f1-4572-8553-89bf3a724deb
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f64b02521fcea9abef9d7196a27e4a209100a892
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="registering-a-legacy-language-service"></a>Registrar un servicio de lenguaje heredado
Las secciones siguientes proporcionan listas de entradas del registro para el idioma diversas opciones de servicio disponibles en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 En la siguiente lista de entradas del registro, *VS Reg raíz* es igual a HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*X.Y*, donde *X.Y* es el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] número de versión.  
  
## <a name="registry-entries-for-language-service-options"></a>Entradas del registro para las opciones de servicio de lenguaje  
 El *VS Reg raíz*\Languages\Language servicios\\*Nombreidioma* clave puede contener los siguientes valores.  
  
|Name|Tipo|Intervalo|Descripción|  
|----------|----------|-----------|-----------------|  
|(Predeterminado)|REG_SZ|*\<GUID >*|GUID del servicio de lenguaje.|  
|LangResID|REG_DWORD|0 x 0 a 0xffff|Identificador de recurso (ResID) para el nombre de texto localizado del idioma de cadena.|  
|Package|REG_SZ|*\<GUID >*|GUID de VSPackage.|  
|ShowCompletion|REG_DWORD|0-1|Especifica si el **la finalización de instrucciones** opciones en el **opciones** cuadro de diálogo están habilitados.|  
|ShowSmartIndent|REG_DWORD|0-1|Especifica si la opción de seleccionar **inteligente** sangría en el **opciones** se habilita el cuadro de diálogo.|  
|RequestStockColors|REG_DWORD|0-1|Especifica si personalizado o colores predeterminados se usan para palabras clave de color.|  
|ShowHotURLs|REG_DWORD|0-1|Especifica si el usuario puede hacer clic en las direcciones URL.|  
|Direcciones URL no activas de forma predeterminada|REG_DWORD|0-1|Especifica la configuración inicial para el **Habilitar navegación a direcciones URL con un solo clic** opción en el **opciones** cuadro de diálogo.|  
|DefaultToInsertSpaces|REG_DWORD|0-1|Especifica si el servicio de lenguaje tiene "Insertar espacios" como su opción de la ficha predeterminada.|  
|ShowDropdownBarOption|REG_DWORD|0-1|Habilita o deshabilita la **barra de navegación** opción en el **opciones** cuadro de diálogo que muestra u oculta el **barra de navegación**.|  
|Solo la ventana de código único|REG_DWORD|0-1|Habilita o deshabilita la **nueva ventana** choice en la **ventana** menú para un servicio de lenguaje.|  
|EnableAdvancedMembersOption|REG_DWORD|0-1|Habilita o deshabilita un **opciones** configuración del cuadro de diálogo para **ocultar miembros avanzados**.|  
|Compatibilidad con CF_HTML|REG_DWORD|0-1|Especifica si el editor permite copiar y pegar de datos HTML.|  
|EnableLineNumbersOption|REG_DWORD|0-1|Especifica si el **números de línea** opciones en el **opciones** cuadro de diálogo está habilitado para un servicio de lenguaje.|  
|HideAdvancedMembersByDefault|REG_DWORD|0-1|Especifica si los miembros avanzados como campos privados están ocultos en las listas de finalización.|  
|ShowBraceCompletion|REG_DWORD|0-1|Especifica si el **llave finalización** opción en el **opciones** se habilita el cuadro de diálogo.|  
  
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
  
## <a name="registry-entries-for-debugger-languages-options"></a>Entradas del registro para opciones de idiomas del depurador  
 El *VS Reg raíz*\Languages\Language servicios\\*Nombreidioma*\Debugger idiomas\\*GUID*\ clave puede incluir lo siguiente valores.  
  
|Name|Tipo|Intervalo|Descripción|  
|----------|----------|-----------|-----------------|  
|(Predeterminado)|REG_SZ|texto|El valor predeterminado se puede utilizar para documentar el nombre del idioma. El nombre de esta clave es un GUID de un evaluador de expresiones que tiene una entrada correspondiente en  *\<VS Reg raíz >*\AD7Metrics\Expression evaluador.|  
  
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
  
## <a name="registry-entries-for-editor-tools-options"></a>Entradas del registro de opciones de herramientas del Editor  
 Puede agregar las claves del registro bajo la clave EditorToolsOptions para páginas de propiedades y los nodos de propiedad. Estas claves y sus valores identifican páginas de propiedades en el **opciones** cuadro de diálogo (en el **herramientas** menú) que se utilizan para configurar el servicio de lenguaje. En el ejemplo siguiente, *nombre de la página* es el nombre de una página de propiedades, y *nombre de nodo* es el nombre de un nodo en el árbol en el **opciones** cuadro de diálogo. La entrada de página y la entrada del nodo deben especificarse por separado.  
  
|Name|Tipo|Intervalo|Descripción|  
|----------|----------|-----------|-----------------|  
|(Predeterminado)|REG_SZ|resID|El nombre para mostrar localizado de esta página de opciones. El nombre puede ser texto literal o #`nnn`, donde `nnn` es un identificador de recurso de cadena en el archivo DLL de VSPackage especificado de satélite.|  
|Package|REG_SZ|*GUID*|El GUID del VSPackage que implemente esta página de opciones.|  
|Página|REG_SZ|*GUID*|El GUID de la página de propiedades para solicitar desde el VSPackage mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> método. Si esta entrada del registro no está presente, la clave del registro describe un nodo, no una página.|  
  
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
  
## <a name="registry-entries-for-file-name-extension-options"></a>Entradas del registro para opciones de extensión de nombre de archivo  
 La entrada para la extensión de archivo debe incluir el punto inicial, por ejemplo ".myext".  
  
|Name|Tipo|Intervalo|Descripción|  
|----------|----------|-----------|-----------------|  
|(Predeterminado)|REG_SZ|*GUID*|GUID del servicio para el servicio de lenguaje predeterminado para este tipo de extensión de nombre de archivo.|  
  
### <a name="example"></a>Ejemplo  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    File Extensions\  
      .cpp\  
        (Default) = {B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}  
```  
  
## <a name="registry-entries-for-editor-options"></a>Entradas del registro de opciones del Editor  
 El *VS Reg raíz*\Editors clave puede contener los siguientes valores:  
  
|Name|Tipo|Intervalo|Descripción|  
|----------|----------|-----------|-----------------|  
|(Predeterminado)|REG_SZ|""|No utilizadas; puede colocar su nombre aquí para obtener documentación.|  
|DefaultToolboxTab|REG_SZ|""|Nombre de la pestaña del cuadro de herramientas para realizar de forma predeterminada cuando el editor está activo.|  
|DisplayName|REG_SZ|resID|Nombre para mostrar en el **abrir con** cuadro de diálogo. El nombre es el identificador de recurso de cadena o un nombre de formato estándar.|  
|ExcludeDefTextEditor|REG_DWORD|0-1|Utilizado para la **abrir con** comando de menú. Si no desea mostrar el editor de texto predeterminado en la lista de editores disponibles para un tipo de archivo específico, establezca este valor en 1.|  
|LinkedEditorGUID|REG_SZ|*\<GUID >*|Se utiliza para cualquier servicio de lenguaje que se puede abrir un archivo con el soporte técnico de la página de códigos. Por ejemplo, cuando abre un archivo .txt utilizando el **abrir con** comando, se proporcionan opciones para usar el editor de código fuente con y sin codificación.<br /><br /> El GUID especificado en el nombre de la subclave es para el generador de editores de página de códigos; el GUID vinculado especificado en esta entrada del Registro específica es para el generador de editores regular. El propósito de esta entrada es que si el IDE no abre un archivo mediante el editor de forma predeterminada, el IDE intentará usar el editor de la siguiente en la lista. Este editor siguiente no debe ser el generador de editores de página de códigos porque este generador del editor es básicamente el mismo que el generador de editores que no se pudo.|  
|Package|REG_SZ|*\<GUID >*|VSPackage GUID para el Id. del nombre para mostrar.|  
  
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
  
## <a name="registry-entries-for-logical-view-options"></a>Entradas del registro de opciones de vista lógica  
 El *VS Reg raíz*\Editors\\*Editor GUI >*\LogicalViews clave puede contener los siguientes valores.  
  
|Name|Tipo|Intervalo|Descripción|  
|----------|----------|-----------|-----------------|  
|(Predeterminado)|REG_SZ||Sin usar.|  
|*\<GUID >*|REG_SZ|""|Clave para las vistas lógicas admitidas. Puede tener tantos valores como sea necesario. El nombre de la entrada del registro es lo que es importante, no el valor, que siempre es una cadena vacía.|  
  
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
  
## <a name="registry-entries-for-editor-extension-options"></a>Entradas del registro para opciones de extensión del Editor  
 El *VS Reg raíz*\Editors\\*Editor GUID*\Extensions clave puede contener los siguientes valores. La extensión de nombre de archivo no incluye el punto inicial.  
  
|Name|Tipo|Intervalo|Descripción|  
|----------|----------|-----------|-----------------|  
|(Predeterminado)|REG_SZ||Sin usar.|  
|*\<ext >*|REG_DWORD|0-0xffffffff|Prioridad relativa de las extensiones. Si dos o más idiomas comparten la misma extensión, se elige el idioma de mayor prioridad.|  
  
 Además, selección de predeterminada del usuario actual para un editor se almacena en HKEY_Current_User\Software\Microsoft\VisualStudio\\*X.Y*\Default editores\\*ext*. El GUID del servicio del lenguaje seleccionado está en la entrada personalizada. Esta opción tiene prioridad para el usuario actual.  
  
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
  
## <a name="registry-entries-for-managed-package-framework-language-service-options"></a>Entradas del registro para las opciones de servicio de lenguaje de Managed Package Framework  
 Las siguientes entradas del registro son específicas de las clases de servicio de managed package framework (MPF) lenguaje. Estas entradas del registro indican la compatibilidad en el servicio de lenguaje para diversas características de IntelliSense y para otras características de edición avanzadas.  
  
 Estas entradas del registro se tiene acceso a través de la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> clase.  
  
|Name|Tipo|Intervalo|Descripción|  
|----------|----------|-----------|-----------------|  
|CodeSense|REG_DWORD|0-1|Compatibilidad con operaciones de IntelliSense.|  
|MatchBraces|REG_DWORD|0-1|Compatibilidad para la coincidencia de pares de lenguaje como llaves, paréntesis y corchetes.|  
|InformaciónRápida|REG_DWORD|0-1|Compatibilidad para la operación de información rápida de IntelliSense.|  
|ShowMatchingBrace|REG_DWORD|0-1|Compatibilidad para mostrar el par de idioma correspondiente en la barra de estado.|  
|MatchBracesAtCaret|REG_DWORD|0-1|Compatibilidad para mostrar pares coincidentes de idioma, normalmente a través de resaltado de los dos elementos.|  
|MaxErrorMessages|REG_DWORD|0-n|El número máximo de errores que se pueden mostrar en el **lista de errores** ventana.|  
|CodeSenseDelay|REG_DWORD|0-n|El número de milisegundos de retraso antes de iniciar cualquier fondo análisis para una operación de IntelliSense.|  
|EnableAsyncCompletion|REG_DWORD|0-1|Soporte técnico para el análisis de segundo plano.|  
|EnableCommenting|REG_DWORD|0-1|Soporte para comentar bloques de texto seleccionados y también implica compatibilidad para eliminar el comentario de texto seleccionado.|  
|EnableFormatSelection|REG_DWORD|0-1|Compatibilidad con formato de texto como sangría automática o ajustar la posición entre llaves.|  
|AutoOutlining|REG_DWORD|0-1|Soporte técnico para la esquematización (áreas que se pueden contraer).|  
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
 [Desarrollo de un servicio de lenguaje heredado](../../extensibility/internals/developing-a-legacy-language-service.md)