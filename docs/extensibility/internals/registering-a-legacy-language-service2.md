---
title: "Registrar un servicio de lenguaje heredado | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "registro, servicios de lenguaje"
  - "Servicios de lenguaje, información del registro"
  - "registro, servicios de lenguaje"
ms.assetid: ca312aa3-f9f1-4572-8553-89bf3a724deb
caps.latest.revision: 24
caps.handback.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
---
# Registrar un servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Las secciones siguientes proporcionan listas de entradas del registro para el idioma de diversas opciones de servicio disponibles en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 En la siguiente lista de entradas del registro, *VS Reg raíz* es igual a HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*X.Y*, donde *X.Y* es el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] número de versión.  
  
## Entradas del registro para las opciones de servicio de lenguaje  
 El *VS Reg raíz*\\Languages\\Language Services\\*Nombreidioma* clave puede contener los siguientes valores.  
  
|Nombre|Tipo|Intervalo|Descripción|  
|------------|----------|---------------|-----------------|  
|\(Predeterminado\)|REG\_SZ|*\< GUID \>*|GUID del servicio de lenguaje.|  
|LangResID|REG\_DWORD|0 x 0 a 0xffff|Cadena de identificador de recurso \(ResID\) para el nombre de texto localizado del idioma.|  
|Paquete|REG\_SZ|*\< GUID \>*|GUID del VSPackage.|  
|ShowCompletion|REG\_DWORD|0\-1|Especifica si el **la finalización de instrucciones** opciones en el **opciones** cuadro de diálogo están habilitados.|  
|ShowSmartIndent|REG\_DWORD|0\-1|Especifica si la opción de seleccionar **Smart** sangría en el **opciones** cuadro de diálogo está habilitado.|  
|RequestStockColors|REG\_DWORD|0\-1|Especifica si personalizado o colores predeterminados se utilizan para palabras clave de color.|  
|ShowHotURLs|REG\_DWORD|0\-1|Especifica si el usuario puede hacer clic en direcciones URL.|  
|Direcciones URL no activas de forma predeterminada|REG\_DWORD|0\-1|Especifica el valor inicial de la **Habilitar navegación a direcciones URL con un solo clic** opción en el **opciones** cuadro de diálogo.|  
|DefaultToInsertSpaces|REG\_DWORD|0\-1|Especifica si el servicio de lenguaje tiene "Insertar espacios" como su opción de la ficha predeterminada.|  
|ShowDropdownBarOption|REG\_DWORD|0\-1|Habilita o deshabilita el **barra de navegación** opción en el **opciones** cuadro de diálogo que muestra u oculta el **barra de navegación**.|  
|Sólo la ventana de código único|REG\_DWORD|0\-1|Habilita o deshabilita el **nueva ventana** choice en el **ventana** menú para un servicio de lenguaje.|  
|EnableAdvancedMembersOption|REG\_DWORD|0\-1|Habilita o deshabilita un **opciones** configuración del cuadro de diálogo para **Ocultar miembros avanzados**.|  
|Compatibilidad con CF\_HTML|REG\_DWORD|0\-1|Especifica si el editor permite copiar y pegar datos HTML.|  
|EnableLineNumbersOption|REG\_DWORD|0\-1|Especifica si el **números de línea** opciones en el **opciones** cuadro de diálogo está habilitado para un servicio de lenguaje.|  
|HideAdvancedMembersByDefault|REG\_DWORD|0\-1|Especifica si los miembros avanzados como campos privados están ocultos en las listas de finalización.|  
|ShowBraceCompletion|REG\_DWORD|0\-1|Especifica si el **finalización de llave** opción en el **opciones** cuadro de diálogo está habilitado.|  
  
### Ejemplo  
  
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
  
## Entradas del registro de opciones de idiomas del depurador  
 El *VS Reg raíz*\\Languages\\Language Services\\*Nombreidioma*\\Debugger Languages\\*GUID*\\ clave puede incluir los siguientes valores.  
  
|Nombre|Tipo|Intervalo|Descripción|  
|------------|----------|---------------|-----------------|  
|\(Predeterminado\)|REG\_SZ|texto|El valor predeterminado se puede utilizar para documentar el nombre del idioma. El nombre de esta clave es un GUID de un evaluador de expresiones que tiene una entrada correspondiente en *\< raíz de Reg VS \>*\\AD7Metrics\\Expression evaluador.|  
  
### Ejemplo  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      C/C++\  
        Debugger Languages\  
          {3A12D0B7-C26C-11D0-B442-00A0244A1DD2}\  
            (Default) = reg_sz:C++  
```  
  
## Entradas del registro de opciones de herramientas del Editor  
 Puede agregar las claves del registro bajo la clave EditorToolsOptions para páginas de propiedades y los nodos de la propiedad. Estas claves y sus valores identifican páginas de propiedades en el **opciones** cuadro de diálogo \(en el **herramientas** menú\) que se utilizan para configurar el servicio de lenguaje. En el ejemplo siguiente, *nombre de la página* es el nombre de una página de propiedades y *nombre de nodo* es el nombre de un nodo en el árbol de la **opciones** cuadro de diálogo. La página y el movimiento de nodo deben especificarse por separado.  
  
|Nombre|Tipo|Intervalo|Descripción|  
|------------|----------|---------------|-----------------|  
|\(Predeterminado\)|REG\_SZ|ResID|El nombre para mostrar localizado de esta página de opciones. El nombre puede ser texto literal o \#`nnn`, donde `nnn` es un identificador de recursos de cadena en el archivo DLL del VSPackage especificado satélite.|  
|Paquete|REG\_SZ|*GUID*|El GUID del VSPackage que implementa esta página de opciones.|  
|Página|REG\_SZ|*GUID*|El GUID de la página de propiedades para solicitar de VSPackage llamando el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> método. Si esta entrada del registro no está presente, la clave del registro describe un nodo, no una página.|  
  
### Ejemplo  
  
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
  
## Entradas del registro de opciones de extensión de nombre de archivo  
 La entrada para la extensión de archivo debe incluir el punto inicial, por ejemplo ".myext".  
  
|Nombre|Tipo|Intervalo|Descripción|  
|------------|----------|---------------|-----------------|  
|\(Predeterminado\)|REG\_SZ|*GUID*|GUID de servicio para el servicio de lenguaje predeterminado para este tipo de extensión de nombre de archivo.|  
  
### Ejemplo  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    File Extensions\  
      .cpp\  
        (Default) = {B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}  
```  
  
## Entradas del registro de opciones del Editor  
 El *VS Reg raíz*\\Editors clave puede contener los siguientes valores:  
  
|Nombre|Tipo|Intervalo|Descripción|  
|------------|----------|---------------|-----------------|  
|\(Predeterminado\)|REG\_SZ|""|No se utiliza; puede colocar su nombre aquí para obtener la documentación.|  
|DefaultToolboxTab|REG\_SZ|""|Nombre de la pestaña del cuadro de herramientas para realizar de forma predeterminada cuando el editor está activo.|  
|DisplayName|REG\_SZ|ResID|Nombre para mostrar en el **Abrir con** cuadro de diálogo. El nombre es el identificador de recurso de cadena o un nombre de formato estándar.|  
|ExcludeDefTextEditor|REG\_DWORD|0\-1|Utilizado para la **Abrir con** comando de menú. Si no desea mostrar el editor de texto predeterminado en la lista de editores disponibles para un tipo de archivo específico, establezca este valor en 1.|  
|LinkedEditorGUID|REG\_SZ|*\< GUID \>*|Se utiliza para cualquier servicio de lenguaje que se puede abrir un archivo con el soporte técnico de la página de códigos. Por ejemplo, al abrir un archivo .txt utilizando el **Abrir con** comando, se ofrecen opciones para usar el editor de código fuente con y sin codificación.<br /><br /> El GUID que especifica el nombre de la subclave es para el generador de editores de la página de códigos; es el GUID vinculado especificado en esta entrada del Registro específica para el generador de editores regular. El propósito de esta entrada es que si el IDE no abre un archivo mediante el editor de forma predeterminada, el IDE intentará utilizar el editor siguiente en la lista. Este editor siguiente no debe ser el generador de editores de página de códigos porque este generador del editor es básicamente el mismo que el generador de editores que no se pudo.|  
|Paquete|REG\_SZ|*\< GUID \>*|VSPackage GUID para el Id. de nombre para mostrar.|  
  
### Ejemplo  
  
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
  
## Entradas del registro de opciones de vista lógico  
 El *VS Reg raíz*\\Editors\\*Editor GUI \>*\\LogicalViews clave puede contener los siguientes valores.  
  
|Nombre|Tipo|Intervalo|Descripción|  
|------------|----------|---------------|-----------------|  
|\(Predeterminado\)|REG\_SZ||No usado.|  
|*\< GUID \>*|REG\_SZ|""|Clave de las vistas lógicas admitidas. Puede tener tantos valores como sea necesario. El nombre de la entrada del registro es lo que es importante, no el valor, que siempre es una cadena vacía.|  
  
### Ejemplo  
  
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
  
## Entradas del registro para las opciones de extensión del Editor  
 El *VS Reg raíz*\\Editors\\*GUID Editor*\\Extensions clave puede contener los siguientes valores. La extensión de nombre de archivo no incluye el punto inicial.  
  
|Nombre|Tipo|Intervalo|Descripción|  
|------------|----------|---------------|-----------------|  
|\(Predeterminado\)|REG\_SZ||No usado.|  
|*\< extensión \>*|REG\_DWORD|0\-0xffffffff.|Prioridad relativa de extensiones. Si dos o más idiomas comparten la misma extensión, se elige el idioma de mayor prioridad.|  
  
 Además, la actual selección del usuario predeterminado para un editor se almacena en HKEY\_Current\_User\\Software\\Microsoft\\VisualStudio\\*X.Y*\\Default Editors\\*ext*. El GUID del servicio del lenguaje seleccionado está en la entrada personalizada. Esto tiene prioridad para el usuario actual.  
  
### Ejemplo  
  
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
  
## Entradas del registro para las opciones de servicio de lenguaje Managed Package Framework  
 Las siguientes entradas del registro son específicas de las clases de servicio de lenguaje de framework \(MPF\) paquete administrado. Estas entradas del registro indican compatibilidad en el servicio de lenguaje para las distintas características de IntelliSense y para otras características de edición avanzadas.  
  
 Estas entradas del registro se tiene acceso a través de la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> clase.  
  
|Nombre|Tipo|Intervalo|Descripción|  
|------------|----------|---------------|-----------------|  
|CodeSense|REG\_DWORD|0\-1|Compatibilidad para las operaciones de IntelliSense.|  
|MatchBraces|REG\_DWORD|0\-1|Compatibilidad con pares de lenguaje como llaves, paréntesis y corchetes.|  
|InformaciónRápida|REG\_DWORD|0\-1|Compatibilidad para la operación de información rápida de IntelliSense.|  
|ShowMatchingBrace|REG\_DWORD|0\-1|Compatibilidad para mostrar el par coincidente de idioma en la barra de estado.|  
|MatchBracesAtCaret|REG\_DWORD|0\-1|Compatibilidad para mostrar los pares coincidentes de lenguaje, normalmente a través de resaltado de los dos elementos.|  
|MaxErrorMessages|REG\_DWORD|0\-n|El número máximo de errores que se pueden mostrar en el **lista de errores** ventana.|  
|CodeSenseDelay|REG\_DWORD|0\-n|El número de milisegundos de retraso antes de iniciar cualquier fondo de análisis para una operación de IntelliSense.|  
|EnableAsyncCompletion|REG\_DWORD|0\-1|Soporte técnico para el análisis de segundo plano.|  
|EnableCommenting|REG\_DWORD|0\-1|Compatibilidad con bloques de texto seleccionados como comentario y también implica la compatibilidad para eliminar el comentario de texto seleccionado.|  
|EnableFormatSelection|REG\_DWORD|0\-1|Compatibilidad con formato de texto como sangría automática o ajustar la posición de las llaves.|  
|AutoOutlining|REG\_DWORD|0\-1|Compatibilidad con esquema \(áreas que se pueden contraer\).|  
|MaxRegions|REG\_DWORD|0\-n|El número máximo de regiones ocultas por archivo.|  
  
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
  
## Vea también  
 [Desarrollar un servicio de lenguaje](../../extensibility/internals/developing-a-legacy-language-service.md)