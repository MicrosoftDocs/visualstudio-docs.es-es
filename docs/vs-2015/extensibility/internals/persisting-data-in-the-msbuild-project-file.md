---
title: Conservación de datos en el archivo de proyecto de MSBuild | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project files, persisting data in
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 059ddc7b9b8fe0de06530af704bb5f7e271f6744
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51749635"
---
# <a name="persisting-data-in-the-msbuild-project-file"></a>Conservación de datos en el archivo de proyecto de MSBuild
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un subtipo de proyecto que necesite conservar datos específicos del subtipo en el archivo de proyecto para su uso posterior. Un subtipo de proyecto utiliza la persistencia de archivo de proyecto para cumplir los requisitos siguientes:  
  
1.  Conservar los datos que se usa como parte de la creación del proyecto. (Para obtener más información sobre Microsoft Build Engine, consulte [MSBuild](http://msdn.microsoft.com/en-us/7c49aba1-ee6c-47d8-9de1-6f29a906e20b).) Puede obtener información relacionada con la compilación:  
  
    1.  Datos de configuración independiente. Es decir, los datos almacenados en los elementos de MSBuild con condiciones en blanco o falta.  
  
    2.  Dependiente de la configuración de datos. Es decir, los datos almacenados en los elementos de MSBuild que se preparan para una configuración de proyecto determinado. Por ejemplo:  
  
        ```  
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
        ```  
  
2.  Conservar los datos que no es relevantes para la compilación. Estos datos se pueden expresar en XML sin formato que no se valida con un esquema XML.  
  
    1.  Datos de configuración independiente.  
  
    2.  Dependiente de la configuración de datos.  
  
## <a name="persisting-build-related-information"></a>Conservación de la información relacionada con la compilación  
 Persistencia de datos útiles para la creación de un proyecto se controla mediante MSBuild. El sistema MSBuild mantiene una tabla maestra de la información relacionada con la compilación. Subtipos de proyecto son responsables de obtener acceso a estos datos para obtener y establecer los valores de propiedad. Subtipos de proyecto también pueden aumentar la tabla de datos relacionadas con la compilación agregando propiedades adicionales que se deben conservar y quitar propiedades, por lo que no se conservan.  
  
 Para modificar los datos de MSBuild, es responsable de recuperar el objeto de propiedad de MSBuild desde el sistema de proyectos base a través de un subtipo de proyecto <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> es una interfaz implementada en el sistema de proyectos de core y las consultas agregación de subtipo de proyecto para él mediante la ejecución de `QueryInterface`.  
  
 El procedimiento siguiente describe los pasos para quitar una propiedad mediante <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>.  
  
#### <a name="to-remove-a-property-from-an-msbuild-project-file"></a>Para quitar una propiedad de un archivo de proyecto de MSBuild  
  
1.  Llame a `QueryInterface` en <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> del subtipo de proyecto.  
  
2.  Llame a <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A> con `pszPropName` establecido en la propiedad que desea quitar.  
  
### <a name="persisting-non-build-related-information"></a>Información relacionada con la compilación no persistente  
 Persistencia de datos en archivos de proyecto que no son importantes para generar se controla a través de <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>.  
  
 Puede implementar <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> en el método main `project subtype aggregator` objeto, el `project subtype project configuration` objeto, o ambos.  
  
 Los puntos siguientes describen los principales conceptos sobre la persistencia de la información relacionada de no compilación.  
  
-   El proyecto base llama a en el objeto de proyecto principal (es decir, el subtipo de proyecto más externo) de subtipo agregador para cargar y guardar datos de configuración independientes, y se llama en los objetos de configuración de proyecto de subtipo de proyecto para cargar o guardar la configuración dependiente datos.  
  
-   El proyecto base llama a los métodos de <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> varias veces para cada nivel de agregación de subtipo de proyecto y pasa el GUID para cada nivel.  
  
-   El proyecto base pasa o recibe un fragmento XML que está dedicado a un subtipo de proyecto en particular y utiliza este mecanismo como una manera de conservar el estado entre los niveles de agregación.  
  
-   El proyecto base llama el subtipo de proyecto más externo <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>implementación pasando un GUID. Si pertenece el GUID del subtipo de proyecto más externo, controla la llamada en Sí; en caso contrario, delega la llamada a un subtipo interno del proyecto y así sucesivamente, hasta que se encuentra el subtipo de proyecto que se corresponde con el GUID.  
  
-   Un subtipo de proyecto también puede modificar el fragmento XML antes o después de que delega la llamada a un subtipo de proyecto interno. El ejemplo siguiente muestra un extracto de un archivo de proyecto, donde un nombre de un archivo que contiene las propiedades específicas de un subtipo de proyecto, se pasa a ese subtipo de proyecto.  
  
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

