---
title: Elementos comunes de proyectos de MSBuild | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, common project items
ms.assetid: 1eba3721-cc12-4b80-9987-84923ede5e2e
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b119cae4013bd1be5657224ad54de54c10321848
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47576102"
---
# <a name="common-msbuild-project-items"></a>Elementos comunes de proyectos de MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [elementos comunes de proyectos de MSBuild](https://docs.microsoft.com/visualstudio/msbuild/common-msbuild-project-items).  
  
  
En [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], un elemento es una referencia con nombre a uno o varios archivos. Los elementos contienen metadatos como nombres de archivo, rutas de acceso y números de versión. Todos los tipos de proyecto de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] tienen varios elementos en común. Estos elementos se definen en el archivo microsoft.build.commontypes.xsd.  
  
## <a name="common-items"></a>Elementos comunes  
 A continuación, se muestra una lista de todos los elementos de proyecto comunes.  
  
### <a name="reference"></a>Referencia  
 Representa una referencia de ensamblado (administrada) del proyecto.  
  
|Nombre del elemento|Descripción|  
|---------------|-----------------|  
|HintPath|Cadena opcional. Ruta de acceso absoluta o relativa del ensamblado.|  
|Name|Cadena opcional. Nombre para mostrar del ensamblado, por ejemplo, "System.Windows.Forms".|  
|FusionName|Cadena opcional. Especifica el nombre de fusión sencillo o seguro del elemento.<br /><br /> Cuando este atributo está presente se ahorra tiempo, ya que no es necesario abrir el archivo de ensamblado para obtener el nombre de fusión.|  
|SpecificVersion|Booleano opcional. Especifica si solo se debe hacer referencia a la versión del nombre de fusión.|  
|Alias|Cadena opcional. Cualquier alias de la referencia.|  
|Private|Booleano opcional. Especifica si la referencia debe copiarse en la carpeta de salida. Este atributo coincide con la propiedad **Copia local** de la referencia que está en el IDE de Visual Studio.|  
  
### <a name="comreference"></a>COMReference  
 Representa una referencia a un componente COM (no administrado) del proyecto.  
  
|Nombre del elemento|Descripción|  
|---------------|-----------------|  
|Name|Cadena opcional. El nombre para mostrar del componente.|  
|Guid|Cadena opcional. GUID del componente, con el formato {12345678-1234-1234-1234-1234567891234}.|  
|VersionMajor|Cadena opcional. Parte principal del número de versión del componente. Por ejemplo, "5" si el número de versión completo es "5.46".|  
|VersionMinor|Cadena opcional. Parte secundaria del número de versión del componente. Por ejemplo, "46" si el número de versión completo es "5.46".|  
|LCID|Cadena opcional. LocaleID del componente.|  
|WrapperTool|Cadena opcional. Nombre de la herramienta contenedor que se usa en el componente, por ejemplo, "tlbimp".|  
|Isolated|Booleano opcional. Especifica si se trata de un componente sin registro.|  
  
### <a name="comfilereference"></a>COMFileReference  
 Representa una lista de las bibliotecas de tipos que se pasan al destino ResolvedComreference.  
  
|Nombre del elemento|Descripción|  
|---------------|-----------------|  
|WrapperTool|Cadena opcional. Nombre de la herramienta contenedor que se usa en el componente, por ejemplo, "tlbimp".|  
  
### <a name="nativereference"></a>NativeReference  
 Representa un archivo de manifiesto nativo o una referencia a este archivo.  
  
|Nombre del elemento|Descripción|  
|---------------|-----------------|  
|Name|Cadena necesaria. Nombre base del archivo de manifiesto.|  
|HintPath|Cadena necesaria. Ruta de acceso relativa del archivo de manifiesto.|  
  
### <a name="projectreference"></a>ProjectReference  
 Representa una referencia a otro proyecto.  
  
|Nombre del elemento|Descripción|  
|---------------|-----------------|  
|Name|Cadena opcional. Nombre para mostrar de la referencia.|  
|Project|Cadena opcional. GUID de la referencia, con el formato {12345678-1234-1234-1234-1234567891234}.|  
|Package|Cadena opcional. Ruta de acceso del archivo de proyecto al que se hace referencia.|  
  
### <a name="compile"></a>Compile  
 Representa los archivos de código fuente para el compilador.  
  
|Nombre del elemento|Descripción|  
|---------------|-----------------|  
|DependentUpon|Cadena opcional. Especifica el archivo del que depende este archivo para compilarse correctamente.|  
|AutoGen|Booleano opcional. Indica si el entorno de desarrollo integrado (IDE) de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ha generado el archivo para el proyecto.|  
|Vínculo|Cadena opcional. Ruta de acceso notacional que se va a mostrar cuando el archivo se encuentre físicamente fuera de la influencia del archivo de proyecto.|  
|Visible|Booleano opcional. Indica si se va a mostrar el archivo en el **Explorador de soluciones** de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|CopyToOutputDirectory|Cadena opcional. Determina si el archivo se va a copiar en el directorio de resultados. Los valores son:<br /><br /> 1.  Nunca<br />2.  Always<br />3.  PreserveNewest|  
  
### <a name="embeddedresource"></a>EmbeddedResource  
 Representa los recursos que se van a incrustar en el ensamblado generado.  
  
|Nombre del elemento|Descripción|  
|---------------|-----------------|  
|DependentUpon|Cadena opcional. Especifica el archivo del que depende este archivo para compilarse correctamente.|  
|Generator|Cadena necesaria. Nombre de cualquier generador de archivos que se ejecute en este elemento.|  
|LastGenOutput|Cadena necesaria. Nombre del archivo creado por cualquier generador de archivos que se ejecutó en este elemento.|  
|CustomToolNamespace|Cadena necesaria. Espacio de nombres en el que cualquier generador de archivos que se ejecute en este elemento debe crear código.|  
|Link|Cadena opcional. La ruta de acceso notacional se muestra si el archivo se encuentra físicamente fuera de la influencia del proyecto.|  
|Visible|Booleano opcional. Indica si se va a mostrar el archivo en el **Explorador de soluciones** de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|CopyToOutputDirectory|Cadena opcional. Determina si el archivo se va a copiar en el directorio de resultados. Los valores son:<br /><br /> 1.  Nunca<br />2.  Always<br />3.  PreserveNewest|  
|LogicalName|Cadena necesaria. Nombre lógico del recurso incrustado.|  
  
### <a name="content"></a>Content  
 Representa archivos que no están compilados en el proyecto pero que podrían incrustarse o publicarse junto con él.  
  
|Nombre del elemento|Descripción|  
|---------------|-----------------|  
|DependentUpon|Cadena opcional. Especifica el archivo del que depende este archivo para compilarse correctamente.|  
|Generator|Cadena necesaria. Nombre de cualquier generador de archivos que se ejecute en este elemento.|  
|LastGenOutput|Cadena necesaria. Nombre del archivo creado por cualquier generador de archivos que se ejecutó en este elemento.|  
|CustomToolNamespace|Cadena necesaria. Espacio de nombres en el que cualquier generador de archivos que se ejecute en este elemento debe crear código.|  
|Link|Booleano opcional. Indica si se va a mostrar el archivo en el **Explorador de soluciones** de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|PublishState|Cadena necesaria. El estado de publicación del contenido:<br /><br /> - Predeterminado<br />- Incluido<br />- Excluido<br />- Archivo de datos<br />- Requisito previo|  
|IsAssembly|Booleano opcional. Especifica si el archivo es un ensamblado.|  
|Visible|Booleano opcional. Indica si se va a mostrar el archivo en el **Explorador de soluciones** de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|CopyToOutputDirectory|Cadena opcional. Determina si el archivo se va a copiar en el directorio de resultados. Los valores son:<br /><br /> 1.  Nunca<br />2.  Always<br />3.  PreserveNewest|  
  
### <a name="none"></a>Ninguna  
 Representa archivos que no deberían tener ningún rol en el proceso de compilación.  
  
|Nombre del elemento|Descripción|  
|---------------|-----------------|  
|DependentUpon|Cadena opcional. Especifica el archivo del que depende este archivo para compilarse correctamente.|  
|Generator|Cadena necesaria. Nombre de cualquier generador de archivos que se ejecute en este elemento.|  
|LastGenOutput|Cadena necesaria. Nombre del archivo creado por cualquier generador de archivos que se ejecutó en este elemento.|  
|CustomToolNamespace|Cadena necesaria. Espacio de nombres en el que cualquier generador de archivos que se ejecute en este elemento debe crear código.|  
|Link|Cadena opcional. Ruta de acceso notacional que se mostrará si el archivo se encuentra físicamente fuera de la influencia del proyecto.|  
|Visible|Booleano opcional. Indica si se va a mostrar el archivo en el **Explorador de soluciones** de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|CopyToOutputDirectory|Cadena opcional. Determina si el archivo se va a copiar en el directorio de resultados. Los valores son:<br /><br /> 1.  Nunca<br />2.  Always<br />3.  PreserveNewest|  
  
### <a name="baseapplicationmanifest"></a>BaseApplicationManifest  
 Representa el manifiesto de aplicación base de la compilación y contiene información de seguridad de implementación de [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)].  
  
### <a name="codeanalysisimport"></a>CodeAnalysisImport  
 Representa el proyecto FxCop que se importará.  
  
### <a name="import"></a>Importar  
 Representa los ensamblados cuyos espacios de nombres debe importar el compilador [!INCLUDE[vbprvb](../includes/vbprvb-md.md)].  
  
## <a name="see-also"></a>Vea también  
 [Propiedades comunes de proyectos de MSBuild](../msbuild/common-msbuild-project-properties.md)



