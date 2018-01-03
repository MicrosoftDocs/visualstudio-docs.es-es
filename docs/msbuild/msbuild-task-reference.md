---
title: Referencia de tareas de MSBuild | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords: MSBuild, tasks
ms.assetid: b3144b27-a426-4259-b8ae-5f7991b202b6
caps.latest.revision: "32"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7ae20ab8aead2369ddd3024c84b66003cf958358
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="msbuild-task-reference"></a>Referencia de tareas de MSBuild
Las tareas proporcionan el código que se ejecuta durante el proceso de compilación. Las tareas de la siguiente lista se incluyen con [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Cuando se instala [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], hay tareas adicionales disponibles que se utilizan para compilar proyectos de [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]. Para obtener más información, consulte [Tareas de MSBuild específicas de Visual C++](../msbuild/msbuild-tasks-specific-to-visual-cpp.md).  
  
 Además de los parámetros mostrados en los temas de esta sección, cada tarea también tiene los parámetros siguientes:  
  
|Parámetro|Description|  
|---------------|-----------------|  
|`Condition`|Parámetro `String` opcional.<br /><br /> Expresión de tipo `Boolean` que el motor de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] emplea para determinar si se ejecutará esta tarea. Para obtener información sobre las condiciones admitidas en [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], vea [Condiciones](../msbuild/msbuild-conditions.md).|  
|`ContinueOnError`|Parámetro opcional. Puede contener uno de los siguientes valores:<br /><br /> -   **WarnAndContinue** o **true**. Cuando se produce un error en una tarea, las tareas subsiguientes en el elemento [Target](../msbuild/target-element-msbuild.md) y la compilación continúan ejecutándose, y todos los errores de la tarea se tratan como advertencias.<br />-   **ErrorAndContinue**. Cuando se produce un error en una tarea, las tareas subsiguientes en el elemento `Target` y la compilación continúan ejecutándose, y todos los errores de la tarea se tratan como errores.<br />-   **ErrorAndStop** o **false** (valor predeterminado). Cuando se produce un error en una tarea, las tareas restantes en el elemento `Target` y la compilación no se ejecutan, y se considera que se ha producido un error en todo el elemento `Target` y la compilación.<br /><br /> Las versiones de .NET Framework anteriores a 4.5 solo admiten los valores `true` y `false`.<br /><br /> Para obtener más información, consulte [Cómo: Pasar errores por alto en las tareas](../msbuild/how-to-ignore-errors-in-tasks.md).|  
  
## <a name="in-this-section"></a>En esta sección  
 [Clase base de tarea](../msbuild/task-base-class.md)  
 Agrega varios parámetros a las tareas que derivan de la clase <xref:Microsoft.Build.Utilities.Task>.  
  
 [Clase base TaskExtension](../msbuild/taskextension-base-class.md)  
 Agrega varios parámetros a las tareas que derivan de la clase <xref:Microsoft.Build.Tasks.TaskExtension>.  
  
 [Clase base ToolTaskExtension](../msbuild/tooltaskextension-base-class.md)  
 Agrega varios parámetros a las tareas que derivan de la clase <xref:Microsoft.Build.Tasks.ToolTaskExtension>.  
  
 [Tarea AL (Assembly Linker)](../msbuild/al-assembly-linker-task.md)  
 Crea un ensamblado con un manifiesto a partir de uno o más archivos que son módulos o archivos de recursos.  
  
 [Tarea AspNetCompiler](../msbuild/aspnetcompiler-task.md)  
 Ajusta aspnet_compiler.exe, una utilidad para precompilar las aplicaciones ASP.NET.  
  
 [Tarea AssignCulture](../msbuild/assignculture-task.md)  
 Asigna identificadores de referencia cultural a los elementos.  
  
 [Tarea AssignProjectConfiguration](../msbuild/assignprojectconfiguration-task.md)  
 Acepta una lista de cadenas de configuración y las asigna a los proyectos especificados.  
  
 [Tarea AssignTargetPath](../msbuild/assigntargetpath-task.md)  
 Acepta una lista de archivos y agrega atributos `<TargetPath>` si aún no se han especificado.  
  
 [Tarea CallTarget](../msbuild/calltarget-task.md)  
 Invoca un destino en el archivo de proyecto.  
  
 [Tarea CombinePath](../msbuild/combinepath-task.md)  
 Combina las rutas de acceso especificadas en una única ruta de acceso.  
  
 [Tarea ConvertToAbsolutePath](../msbuild/converttoabsolutepath-task.md)  
 Convierte una ruta de acceso relativa o una referencia en una ruta de acceso absoluta.  
  
 [Tarea Copy](../msbuild/copy-task.md)  
 Copia archivos a una nueva ubicación.  
  
 [Tarea CreateCSharpManifestResourceName](../msbuild/createcsharpmanifestresourcename-task.md)  
 Crea el nombre de un manifiesto de estilo [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] a partir del nombre de un archivo .resx especificado u otro recurso.  
  
 [Tarea CreateItem](../msbuild/createitem-task.md)  
 Rellena colecciones de elementos a partir de los elementos de entrada, permitiendo copiar elementos de una lista a otra.  
  
 [Tarea CreateProperty](../msbuild/createproperty-task.md)  
 Rellena propiedades a partir de los valores de entrada, permitiendo copiar valores de una propiedad o cadena a otra.  
  
 [Tarea CreateVisualBasicManifestResourceName](../msbuild/createvisualbasicmanifestresourcename-task.md)  
 Crea el nombre de un manifiesto de estilo [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] a partir del nombre de un archivo .resx especificado u otro recurso.  
  
 [Tarea Csc](../msbuild/csc-task.md)  
 Invoca el compilador de Visual C# para generar archivos ejecutables, bibliotecas de vínculos dinámicos o módulos de código.  
  
 [Tarea Delete](../msbuild/delete-task.md)  
 Elimina los archivos especificados.  
  
 [Tarea Error](../msbuild/error-task.md)  
 Detiene una compilación y registra un error basándose en una instrucción condicional evaluada.  
  
 [Tarea Exec](../msbuild/exec-task.md)  
 Ejecuta el programa o comando especificado con los argumentos especificados.  
  
 [Tarea FindAppConfigFile](../msbuild/findappconfigfile-task.md)  
 Busca el archivo app.config, si hay alguno, en las listas proporcionadas.  
  
 [Tarea FindInList](../msbuild/findinlist-task.md)  
 Busca un elemento en una lista especificada con las especificaciones coincidentes.  
  
 [Tarea FindUnderPath](../msbuild/findunderpath-task.md)  
 Determina los elementos de la colección de elementos especificada existen en la carpeta especificada y todas las subcarpetas.  
  
 [Tarea FormatUrl](../msbuild/formaturl-task.md)  
 Convierte una dirección URL en un formato de dirección URL correcto.  
  
 [Tarea FormatVersion](../msbuild/formatversion-task.md)  
 Anexa el número de revisión al número de versión.  
  
 [Tarea GenerateApplicationManifest](../msbuild/generateapplicationmanifest-task.md)  
 Genera un manifiesto de aplicación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] o un manifiesto nativo.  
  
 [Tarea GenerateBootstrapper](../msbuild/generatebootstrapper-task.md)  
 Proporciona una forma automatizada de detectar, descargar e instalar una aplicación y sus requisitos previos.  
  
 [Tarea GenerateDeploymentManifest](../msbuild/generatedeploymentmanifest-task.md)  
 Genera un manifiesto de implementación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
 [Tarea GenerateResource](../msbuild/generateresource-task.md)  
 Convierte archivos .txt y .resx en archivos .resources binarios de Common Language Runtime.  
  
 [Tarea GenerateTrustInfo](../msbuild/generatetrustinfo-task.md)  
 Genera la información de confianza de la aplicación a partir del manifiesto base y de los parámetros `TargetZone` y `ExcludedPermissions`.  
  
 [Tarea GetAssemblyIdentity](../msbuild/getassemblyidentity-task.md)  
 Recupera las identidades de ensamblado de los archivos especificados y genera la información de identidad.  
  
 [Tarea GetFrameworkPath](../msbuild/getframeworkpath-task.md)  
 Recupera la ruta de acceso a los ensamblados de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 [Tarea GetFrameworkSdkPath](../msbuild/getframeworksdkpath-task.md)  
 Recupera la ruta de acceso a [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)].  
  
 [Tarea GetReferenceAssemblyPaths](../msbuild/getreferenceassemblypaths-task.md)  
 Devuelve las rutas de acceso al ensamblado de referencia de las diversas plataformas.  
  
 [Tarea LC](../msbuild/lc-task.md)  
 Genera un archivo .license a partir de un archivo .licx.  
  
 [Tarea MakeDir](../msbuild/makedir-task.md)  
 Crea directorios y, si es preciso, cualquier directorio primario.  
  
 [Tarea Message](../msbuild/message-task.md)  
 Registra un mensaje durante una compilación.  
  
 [Tarea Move](../msbuild/move-task.md)  
 Mueve los archivos a una nueva ubicación.  
  
 [Tarea de MSBuild](../msbuild/msbuild-task.md)  
 Compila proyectos de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] desde otro proyecto de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
 [Tarea ReadLinesFromFile](../msbuild/readlinesfromfile-task.md)  
 Lee una lista de elementos de un archivo de texto.  
  
 [Tarea RegisterAssembly](../msbuild/registerassembly-task.md)  
 Lee los metadatos dentro del ensamblado especificado y agrega las entradas necesarias al Registro.  
  
 [Tarea RemoveDir](../msbuild/removedir-task.md)  
 Quita los directorios especificados y todos sus archivos y subdirectorios.  
  
 [Tarea RemoveDuplicates](../msbuild/removeduplicates-task.md)  
 Quita los elementos duplicados de la colección de elementos especificada.  
  
 [Tarea RequiresFramework35SP1Assembly](../msbuild/requiresframework35sp1assembly-task.md)  
 Determina si la aplicación requiere .NET Framework 3.5 SP1.  
  
 ResGen (Tarea)  
 Obsoleto. Utilice la tarea [GenerateResource (Tarea)](../msbuild/generateresource-task.md) para convertir archivos .txt y .resx desde y hacia archivos .resources binarios de Common Language Runtime.  
  
 [Tarea ResolveAssemblyReference](../msbuild/resolveassemblyreference-task.md)  
 Determina todos los ensamblados que dependen de los ensamblados especificados.  
  
 [Tarea ResolveComReference](../msbuild/resolvecomreference-task.md)  
 Toma una lista de uno o varios nombres de biblioteca de tipos o archivos .tlb y resuelve esas bibliotecas de tipos en ubicaciones de disco.  
  
 [Tarea ResolveKeySource](../msbuild/resolvekeysource-task.md)  
 Determina el origen de la clave de nombre seguro.  
  
 [Tarea ResolveManifestFiles](../msbuild/resolvemanifestfiles-task.md)  
 Resuelve los siguientes elementos en el proceso de compilación de los archivos para la generación de manifiestos: elementos compilados, dependencias, ensamblados satélite, contenido, símbolos de depuración y documentación.  
  
 [Tarea ResolveNativeReference](../msbuild/resolvenativereference-task.md)  
 Resuelve las referencias nativas.  
  
 [Tarea ResolveNonMSBuildProjectOutput](../msbuild/resolvenonmsbuildprojectoutput-task.md)  
 Determina los archivos de salida de las referencias de proyecto que no son de MSBuild.  
  
 [Tarea SGen](../msbuild/sgen-task.md)  
 Crea un ensamblado de serialización XML para los tipos del ensamblado especificado.  
  
 [Tarea SignFile](../msbuild/signfile-task.md)  
 Firma un archivo determinado con el certificado especificado.  
  
 [Tarea Touch](../msbuild/touch-task.md)  
 Establece la hora de acceso y de modificación de los archivos.  
  
 [Tarea UnregisterAssembly](../msbuild/unregisterassembly-task.md)  
 Elimina del Registro los ensamblados especificados para la interoperabilidad COM.  
  
 [Tarea UpdateManifest](../msbuild/updatemanifest-task.md)  
 Actualiza las propiedades seleccionadas en un manifiesto y se retira.  
  
 [Tarea Vbc](../msbuild/vbc-task.md)  
 Invoca el compilador de Visual Basic para generar archivos ejecutables, bibliotecas de vínculos dinámicos o módulos de código.  
  
 [Tarea Warning](../msbuild/warning-task.md)  
 Registra una advertencia durante la compilación basándose en una instrucción condicional evaluada.  
  
 [Tarea WriteCodeFragment](../msbuild/writecodefragment-task.md)  
 Genera un archivo de código temporal usando el fragmento de código generado especificado. No elimina el archivo.  
  
 [Tarea WriteLinesToFile](../msbuild/writelinestofile-task.md)  
 Escribe los elementos especificados en el archivo de texto especificado.  
  
 [Tarea XmlPeek](../msbuild/xmlpeek-task.md)  
 Devuelve valores conforme a lo que especifica una consulta XPath de un archivo XML.  
  
 [Tarea XmlPoke](../msbuild/xmlpoke-task.md)  
 Establece los valores especificados por una consulta XPath en un archivo XML.  
  
 [Tarea XslTransformation](../msbuild/xsltransformation-task.md)  
 Transforma una entrada XML utilizando un *Lenguaje de transformación basado en hojas de estilo* (XSLT) o un XSLT compilado y envía los resultados a un dispositivo de salida o un archivo.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de MSBuild](../msbuild/msbuild-reference.md)   
 [Escribir tareas](../msbuild/task-writing.md)   
 [Tareas](../msbuild/msbuild-tasks.md)