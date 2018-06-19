---
title: Almacenar datos en el archivo de proyecto de MSBuild | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project files, persisting data in
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 324f9dfd4e381e9580e4940f06f652ef64d9d3ec
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132085"
---
# <a name="persisting-data-in-the-msbuild-project-file"></a>Almacenar datos en el archivo de proyecto de MSBuild
Un subtipo de proyecto que necesite conservar datos específicos del subtipo en el archivo de proyecto para su uso posterior. Un subtipo de proyecto usa la persistencia del archivo de proyecto para cumplir los requisitos siguientes:  
  
1.  Conservar los datos que se usa como parte de la generación del proyecto. (Para obtener más información sobre Microsoft Build Engine, consulte [MSBuild](../../msbuild/msbuild.md).) Puede obtener información relacionada con la compilación:  
  
    1.  Datos de configuración independiente. Es decir, los datos almacenados en los elementos de MSBuild y condiciones en blanco o falta.  
  
    2.  Dependiendo de la configuración de datos. Es decir, los datos almacenados en los elementos de MSBuild que se preparan para una configuración de proyecto determinado. Por ejemplo:  
  
        ```  
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
        ```  
  
2.  Conservar los datos que no es relevantes para la compilación. Estos datos se pueden expresar en XML de forma libre que no se valida con un esquema XML.  
  
    1.  Datos de configuración independiente.  
  
    2.  Dependiendo de la configuración de datos.  
  
## <a name="persisting-build-related-information"></a>Conservar información relacionada con la compilación  
 Persistencia de datos útiles para la creación de un proyecto se controla mediante MSBuild. El sistema MSBuild mantiene una tabla maestra de la información relacionada con la compilación. Subtipos de proyecto son responsables de obtener acceso a estos datos para obtener y establecer valores de propiedad. Subtipos de proyecto también pueden aumentar la tabla de datos relacionadas con la compilación agregando propiedades adicionales que se deben conservar y quitar propiedades de modo que no se conservan.  
  
 Para modificar los datos de MSBuild, es responsable de recuperar el objeto de propiedad de MSBuild desde el sistema del proyecto de base a través de un subtipo de proyecto <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> es una interfaz implementada en el sistema del proyecto principal y la agregación consultas subtipo de proyecto para él mediante la ejecución de `QueryInterface`.  
  
 El procedimiento siguiente describe los pasos para quitar una propiedad mediante <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>.  
  
#### <a name="to-remove-a-property-from-an-msbuild-project-file"></a>Para quitar una propiedad de un archivo de proyecto de MSBuild  
  
1.  Llame a `QueryInterface` en <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> del subtipo de proyecto.  
  
2.  Llame a <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A> con `pszPropName` establecido en la propiedad que desea quitar.  
  
### <a name="persisting-non-build-related-information"></a>Información relacionada con la compilación no persistente  
 Persistencia de los datos en los archivos de proyecto que no es relevante generar se controla a través de <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>.  
  
 Puede implementar <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> en el método main `project subtype aggregator` objeto, el `project subtype project configuration` objeto, o ambos.  
  
 Los puntos siguientes describen los principales conceptos sobre la persistencia de la información de compilación no relacionado.  
  
-   El proyecto de base llama en el objeto de agregador de subtipo (es decir, el subtipo de proyecto más externa) de proyecto principal para cargar y guardar datos de configuración independientes, y llama en los objetos de configuración del proyecto de subtipo de proyecto para cargar o guardar dependientes de la configuración datos.  
  
-   El proyecto de base llama a los métodos de <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> varias veces para cada nivel de agregación de subtipo de proyecto y pasa el GUID para cada nivel.  
  
-   El proyecto de base se pasa o recibe un fragmento XML que se dedica a un subtipo de proyecto determinado y utiliza este mecanismo como una manera de mantener el estado entre los niveles de agregación.  
  
-   El proyecto de base llama el subtipo de proyecto exterior <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>implementación pasando un GUID. Si el GUID pertenece a del subtipo de proyecto más externo, controla la llamada en Sí; en caso contrario, delega la llamada a un subtipo de proyecto interna y así sucesivamente, hasta que se encuentra el subtipo de proyecto que se corresponde con el GUID.  
  
-   Un subtipo de proyecto también puede modificar el fragmento XML antes o después de que delega la llamada a un subtipo de proyecto interna. En el ejemplo siguiente se muestra un extracto de un archivo de proyecto, donde un nombre de un archivo que contiene propiedades específicas de un subtipo de proyecto, se pasa a ese subtipo de proyecto.  
  
    ```  
    <ProjectExtensions>  
        <VisualStudio>  
          <FlavorProperties GUID="{<FlavorGUID>}">  
            <FlavorProject TestFileFolder="TestFile" />  
          </FlavorProperties>  
        </VisualStudio>  
      </ProjectExtensions>  
    ```  
  
## <a name="see-also"></a>Vea también  
 [Subtipos de proyecto](../../extensibility/internals/project-subtypes.md)