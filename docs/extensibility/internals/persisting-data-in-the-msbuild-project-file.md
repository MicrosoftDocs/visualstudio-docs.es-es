---
title: "Conservar los datos en el archivo de proyecto de MSBuild | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "archivos de proyecto, conservar los datos en"
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Conservar los datos en el archivo de proyecto de MSBuild
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un subtipo del proyecto puede necesitar conservar los datos subtipo\-específicos en el archivo de proyecto para su uso posterior.  Un subtipo de proyectos utiliza la persistencia del archivo de proyecto para cumplir los requisitos siguientes:  
  
1.  Conserve los datos utilizados como parte de la compilación del proyecto.  \(Para obtener más información sobre Microsoft Build Engine, vea [MSBuild](http://msdn.microsoft.com/es-es/7c49aba1-ee6c-47d8-9de1-6f29a906e20b).\) información relacionada con puede cualquiera:  
  
    1.  datos de la independientes.  es decir, datos almacenados en los elementos de MSBuild con el espacio en blanco o condiciones que falta.  
  
    2.  datos dependientes.  es decir, datos almacenados en los elementos de MSBuild que se condicionan para una configuración de proyecto determinada.  Por ejemplo:  
  
        ```  
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
        ```  
  
2.  Conserve los datos que no son pertinentes para compilar.  Estos datos se pueden expresar en XML de forma libre que no se valida con un esquema XML.  
  
    1.  datos de la independientes.  
  
    2.  datos dependientes.  
  
## Información relacionada con de persistencia  
 La persistencia de los datos útiles para compilar un proyecto se administra con MSBuild.  El sistema MSBuild mantiene una tabla principal de información relacionada con.  Los subtipos de proyecto son responsables de obtener acceso a estos datos para obtener y establecer valores de propiedad.  Los subtipos de proyectos también pueden aumentar la tabla de datos relacionada con agregando propiedades adicionales que se persistirán y quitar propiedades para que no se conservan.  
  
 Para modificar los datos de MSBuild, un subtipo del proyecto es responsable de recuperar el objeto de propiedad de MSBuild del sistema base del proyecto con <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> es una interfaz implementada en el sistema de proyectos básico y las consultas de subtipo del proyecto que agregan para ejecutando `QueryInterface`.  
  
 El procedimiento siguiente describe los pasos para quitar una propiedad mediante <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>.  
  
#### para quitar una propiedad de un archivo de proyecto de MSBuild  
  
1.  Llame a `QueryInterface` en <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> de subtipo del proyecto.  
  
2.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A> de llamada con `pszPropName` establecido en la propiedad que desea quitar.  
  
### información relacionada de persistencia de la No\-Generación  
 La persistencia de los datos en archivos de proyecto que no importa para compilar se administra con <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>.  
  
 Puede implementar <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> en el objeto principal de `project subtype aggregator` , el objeto de `project subtype project configuration` , o ambos.  
  
 Los puntos siguientes describen los principales conceptos relativos al conservar la información relacionada con la no\-generación.  
  
-   Las llamadas bases del proyecto en el objeto principal del agregador de subtipo del proyecto \(es decir, subtipo fuera del proyecto\) para cargar y guardar datos independientes de la configuración, y ésta llama a los objetos de configuración de proyecto de subtipo del proyecto para cargar o guardar datos dependientes de la configuración.  
  
-   El proyecto base llama a los métodos de varias veces <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> para cada nivel de agregación de subtipo del proyecto, y pasa el GUID para cada capa.  
  
-   El proyecto base pasa o recibe un fragmento XML dedicado a un subtipo concreto del proyecto y use este mecanismo como forma de estado de persistencia entre los niveles de agregación.  
  
-   El proyecto base llama a la implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>de subtipo fuera del proyecto que pasa el GUID.  Si el GUID pertenece al subtipo fuera del proyecto, controla la llamada propio; si no delega la llamada en un subtipo interno del proyecto, y así sucesivamente, hasta que encuentre el subtipo de proyecto al que GUID corresponde.  
  
-   Un subtipo del proyecto también puede modificar el fragmento XML antes o después de que delega la llamada en un subtipo interno del proyecto.  El ejemplo siguiente se muestra un fragmento de un archivo de proyecto, donde un nombre de un archivo que contiene las propiedades específicas de un subtipo del proyecto, se pasa al subtipo del proyecto.  
  
    ```  
    <ProjectExtensions>  
        <VisualStudio>  
          <FlavorProperties GUID="{<FlavorGUID>}">  
            <FlavorProject TestFileFolder="TestFile" />  
          </FlavorProperties>  
        </VisualStudio>  
      </ProjectExtensions>  
    ```  
  
## Vea también  
 [Subtipos de proyecto](../../extensibility/internals/project-subtypes.md)