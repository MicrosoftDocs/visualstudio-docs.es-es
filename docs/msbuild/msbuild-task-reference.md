---
title: Referencia de tareas de MSBuild | Microsoft Docs
description: Obtenga información sobre las tareas que se incluyen con MSBuild, que proporcionan código que se ejecuta durante el proceso de compilación.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tasks
ms.assetid: b3144b27-a426-4259-b8ae-5f7991b202b6
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f26c3c1b8256597c795fa8bcd815fd605f895fa5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878388"
---
# <a name="msbuild-task-reference"></a>Referencia de tareas de MSBuild

Las tareas proporcionan el código que se ejecuta durante el proceso de compilación. Las tareas de la siguiente lista se incluyen con MSBuild. Cuando se instala carga de trabajo de C++, hay tareas adicionales disponibles que se utilizan para compilar proyectos de C++. Para más información, consulte [Tareas de C++](../msbuild/msbuild-tasks-specific-to-visual-cpp.md).

Además de los parámetros mostrados en los temas de esta sección, cada tarea también tiene los parámetros siguientes:

| Parámetro | Descripción |
|-------------------| - |
| `Condition` | Parámetro `String` opcional.<br /><br /> Expresión de tipo `Boolean` que el motor de MSBuild emplea para determinar si se ejecutará esta tarea. Para obtener información sobre las condiciones admitidas en MSBuild, vea [Condiciones](../msbuild/msbuild-conditions.md). |
| `ContinueOnError` | Parámetro opcional. Puede contener uno de los siguientes valores:<br /><br /> -   **WarnAndContinue** o **true**. Cuando se produce un error en una tarea, las tareas subsiguientes en el elemento [Target](../msbuild/target-element-msbuild.md) y la compilación continúan ejecutándose, y todos los errores de la tarea se tratan como advertencias.<br />-   **ErrorAndContinue**. Cuando se produce un error en una tarea, las tareas subsiguientes en el elemento `Target` y la compilación continúan ejecutándose, y todos los errores de la tarea se tratan como errores.<br />-   **ErrorAndStop** o **false** (valor predeterminado). Cuando se produce un error en una tarea, las tareas restantes en el elemento `Target` y la compilación no se ejecutan, y se considera que se ha producido un error en todo el elemento `Target` y la compilación.<br /><br /> Las versiones de .NET Framework anteriores a 4.5 solo admiten los valores `true` y `false`.<br /><br /> Para obtener más información, vea [Cómo: Pasar errores por alto en las tareas](../msbuild/how-to-ignore-errors-in-tasks.md). |

## <a name="in-this-section"></a>En esta sección

- [Clase base Task](../msbuild/task-base-class.md)

 Agrega varios parámetros a las tareas que derivan de la clase <xref:Microsoft.Build.Utilities.Task>. No se debe usar directamente.

- [Clase base TaskExtension](../msbuild/taskextension-base-class.md)

 Agrega varios parámetros a las tareas que derivan de la clase <xref:Microsoft.Build.Tasks.TaskExtension>. No se debe usar directamente.

- [Clase base ToolTaskExtension](../msbuild/tooltaskextension-base-class.md)

 Agrega varios parámetros a las tareas que derivan de la clase <xref:Microsoft.Build.Tasks.ToolTaskExtension>. No se debe usar directamente.

- [AL (Assembly Linker, Tarea)](../msbuild/al-assembly-linker-task.md)

 Crea un ensamblado con un manifiesto a partir de uno o más archivos que son módulos o archivos de recursos.

- [AspNetCompiler (tarea)](../msbuild/aspnetcompiler-task.md)

 Incluye *aspnet_compiler.exe*, una utilidad para precompilar las aplicaciones ASP.NET.

- [AssignCulture (tarea)](../msbuild/assignculture-task.md)

 Asigna identificadores de referencia cultural a los elementos.

- [AssignProjectConfiguration (Tarea)](../msbuild/assignprojectconfiguration-task.md)

 Acepta una lista de cadenas de configuración y las asigna a los proyectos especificados.

- [Tarea AssignTargetPath](../msbuild/assigntargetpath-task.md)

 Acepta una lista de archivos y agrega atributos `<TargetPath>` si aún no se han especificado.

- [CallTarget (tarea)](../msbuild/calltarget-task.md)

 Invoca un destino en el archivo de proyecto.

- [CombinePath (tarea)](../msbuild/combinepath-task.md)

 Combina las rutas de acceso especificadas en una única ruta de acceso.

- [ConvertToAbsolutePath (tarea)](../msbuild/converttoabsolutepath-task.md)

 Convierte una ruta de acceso relativa o una referencia en una ruta de acceso absoluta.

- [Copy (tarea)](../msbuild/copy-task.md)

 Copia archivos a una nueva ubicación.

- [CreateCSharpManifestResourceName (tarea)](../msbuild/createcsharpmanifestresourcename-task.md)

 Crea el nombre de un manifiesto de estilo C# a partir del nombre de un archivo *.resx* determinado u otro recurso.

- [CreateItem (tarea)](../msbuild/createitem-task.md)

 Rellena colecciones de elementos a partir de los elementos de entrada, permitiendo copiar elementos de una lista a otra.

- [CreateProperty (tarea)](../msbuild/createproperty-task.md)

 Rellena propiedades a partir de los valores de entrada, permitiendo copiar valores de una propiedad o cadena a otra.

- [CreateVisualBasicManifestResourceName (tarea)](../msbuild/createvisualbasicmanifestresourcename-task.md)

 Crea el nombre de un manifiesto de estilo Visual Basic a partir del nombre de un archivo *.resx* determinado u otro recurso.

- [Tarea Csc](../msbuild/csc-task.md)

 Invoca el compilador de Visual C# para generar archivos ejecutables, bibliotecas de vínculos dinámicos o módulos de código.

- [Delete (tarea)](../msbuild/delete-task.md)

 Elimina los archivos especificados.

- [DownloadFile (Tarea)](../msbuild/downloadfile-task.md)

 Descarga un archivo a la ubicación especificada.

- [Error (tarea)](../msbuild/error-task.md)

 Detiene una compilación y registra un error basándose en una instrucción condicional evaluada.

- [Exec (tarea)](../msbuild/exec-task.md)

 Ejecuta el programa o comando especificado con los argumentos especificados.

- [FindAppConfigFile (tarea)](../msbuild/findappconfigfile-task.md)

 Busca el archivo *app.config*, si hay alguno, en las listas proporcionadas.

- [FindInList (tarea)](../msbuild/findinlist-task.md)

 Busca un elemento en una lista especificada con las especificaciones coincidentes.

- [FindUnderPath (tarea)](../msbuild/findunderpath-task.md)

 Determina los elementos de la colección de elementos especificada existen en la carpeta especificada y todas las subcarpetas.

- [FormatUrl (tarea)](../msbuild/formaturl-task.md)

 Convierte una dirección URL en un formato de dirección URL correcto.

- [Tarea FormatVersion](../msbuild/formatversion-task.md)

 Anexa el número de revisión al número de versión.

- [GenerateApplicationManifest (tarea)](../msbuild/generateapplicationmanifest-task.md)

 Genera un manifiesto de aplicación de ClickOnce o un manifiesto nativo.

- [GenerateBootstrapper (tarea)](../msbuild/generatebootstrapper-task.md)

 Proporciona una forma automatizada de detectar, descargar e instalar una aplicación y sus requisitos previos.

- [GenerateDeploymentManifest (tarea)](../msbuild/generatedeploymentmanifest-task.md)

 Genera un manifiesto de una implementación de ClickOnce.

- [GenerateResource (tarea)](../msbuild/generateresource-task.md)

 Convierte archivos *.txt* y *.resx* en archivos *.resources* binarios de Common Language Runtime.

- [GenerateTrustInfo (tarea)](../msbuild/generatetrustinfo-task.md)

 Genera la información de confianza de la aplicación a partir del manifiesto base y de los parámetros `TargetZone` y `ExcludedPermissions`.

- [GetAssemblyIdentity (tarea)](../msbuild/getassemblyidentity-task.md)

 Recupera las identidades de ensamblado de los archivos especificados y genera la información de identidad.

- [Tarea GetFileHash](../msbuild/getfilehash-task.md)

 Calcula las sumas de comprobación del contenido de un archivo o conjunto de archivos.

- [GetFrameworkPath (tarea)](../msbuild/getframeworkpath-task.md)

 Recupera la ruta de acceso a los ensamblados de .NET Framework.

- [GetFrameworkSdkPath (tarea)](../msbuild/getframeworksdkpath-task.md)

 Recupera la ruta de acceso del kit de desarrollo de software (SDK) de Windows.

- [GetReferenceAssemblyPaths (Tarea)](../msbuild/getreferenceassemblypaths-task.md)

 Devuelve las rutas de acceso al ensamblado de referencia de las diversas plataformas.

- [LC (tarea)](../msbuild/lc-task.md)

 Genera un archivo *.license* a partir de un archivo *.licx*.

- [MakeDir (tarea)](../msbuild/makedir-task.md)

 Crea directorios y, si es preciso, cualquier directorio primario.

- [Message (tarea)](../msbuild/message-task.md)

 Registra un mensaje durante una compilación.

- [Move (tarea)](../msbuild/move-task.md)

 Mueve los archivos a una nueva ubicación.

- [tareas de MSBuild](../msbuild/msbuild-task.md)

 Compila proyectos de MSBuild desde otro proyecto de MSBuild.

- [ReadLinesFromFile (tarea)](../msbuild/readlinesfromfile-task.md)

 Lee una lista de elementos de un archivo de texto.

- [RegisterAssembly (tarea)](../msbuild/registerassembly-task.md)

 Lee los metadatos dentro del ensamblado especificado y agrega las entradas necesarias al Registro.

- [Tarea RemoveDir](../msbuild/removedir-task.md)

 Quita los directorios especificados y todos sus archivos y subdirectorios.

- [RemoveDuplicates (tarea)](../msbuild/removeduplicates-task.md)

 Quita los elementos duplicados de la colección de elementos especificada.

- [RequiresFramework35SP1Assembly (tarea)](../msbuild/requiresframework35sp1assembly-task.md)

 Determina si la aplicación requiere .NET Framework 3.5 SP1.

- ResGen (Tarea)

 Obsoleto. Utilice la tarea [GenerateResource](../msbuild/generateresource-task.md) para convertir archivos *.txt* y *.resx* desde y hacia archivos *.resources* binarios de Common Language Runtime.

- [ResolveAssemblyReference (tarea)](../msbuild/resolveassemblyreference-task.md)

 Determina todos los ensamblados que dependen de los ensamblados especificados.

- [Tarea ResolveComReference](../msbuild/resolvecomreference-task.md)

 Toma una lista de uno o varios nombres de biblioteca de tipos o archivos *.tlb* y resuelve esas bibliotecas de tipos en ubicaciones de disco.

- [ResolveKeySource (tarea)](../msbuild/resolvekeysource-task.md)

 Determina el origen de la clave de nombre seguro.

- [ResolveManifestFiles (tarea)](../msbuild/resolvemanifestfiles-task.md)

 Resuelve los siguientes elementos en el proceso de compilación de los archivos para la generación de manifiestos: elementos compilados, dependencias, ensamblados satélite, contenido, símbolos de depuración y documentación.

- [ResolveNativeReference (tarea)](../msbuild/resolvenativereference-task.md)

 Resuelve las referencias nativas.

- [ResolveNonMSBuildProjectOutput (tarea)](../msbuild/resolvenonmsbuildprojectoutput-task.md)

 Determina los archivos de salida de las referencias de proyecto que no son de MSBuild.

- [SGen (tarea)](../msbuild/sgen-task.md)

 Crea un ensamblado de serialización XML para los tipos del ensamblado especificado.

- [SignFile (tarea)](../msbuild/signfile-task.md)

 Firma un archivo determinado con el certificado especificado.

- [Touch (tarea)](../msbuild/touch-task.md)

 Establece la hora de acceso y de modificación de los archivos.

- [UnregisterAssembly (tarea)](../msbuild/unregisterassembly-task.md)

 Elimina del Registro los ensamblados especificados para la interoperabilidad COM.

- [Tarea Unzip](../msbuild/unzip-task.md)

 Descomprime un archivo *.zip* en la ubicación especificada.

- [UpdateManifest (tarea)](../msbuild/updatemanifest-task.md)

 Actualiza las propiedades seleccionadas en un manifiesto y se retira.

- [Vbc (Tarea)](../msbuild/vbc-task.md)

 Invoca el compilador de Visual Basic para generar archivos ejecutables, bibliotecas de vínculos dinámicos o módulos de código.

- [Tarea VerifyFileHash](../msbuild/verifyfilehash-task.md)

 Comprueba que un archivo coincide con el hash de archivo esperado.

- [Warning (tarea)](../msbuild/warning-task.md)

 Registra una advertencia durante la compilación basándose en una instrucción condicional evaluada.

- [WriteCodeFragment (tarea)](../msbuild/writecodefragment-task.md)

 Genera un archivo de código temporal usando el fragmento de código generado especificado. No elimina el archivo.

- [WriteLinesToFile (tarea)](../msbuild/writelinestofile-task.md)

 Escribe los elementos especificados en el archivo de texto especificado.

- [XmlPeek (tarea)](../msbuild/xmlpeek-task.md)

 Devuelve valores conforme a lo que especifica una consulta XPath de un archivo XML.

- [XmlPoke (tarea)](../msbuild/xmlpoke-task.md)

 Establece los valores especificados por una consulta XPath en un archivo XML.

- [XslTransformation (tarea)](../msbuild/xsltransformation-task.md)

 Transforma una entrada XML utilizando un *Lenguaje de transformación basado en hojas de estilo* (XSLT) o un XSLT compilado y envía los resultados a un dispositivo de salida o un archivo.

- [Tarea ZipDirectory](../msbuild/zipdirectory-task.md)

 Crea un archivo *.zip* desde el contenido de un directorio.

## <a name="see-also"></a>Vea también

- [Referencia de MSBuild](../msbuild/msbuild-reference.md)
- [Escribir tareas](../msbuild/task-writing.md)
- [Tareas](../msbuild/msbuild-tasks.md)
