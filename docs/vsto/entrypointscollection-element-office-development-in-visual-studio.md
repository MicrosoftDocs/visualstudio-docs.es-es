---
title: '&lt;entryPointsCollection&gt; elemento (desarrollo de Office en Visual Studio) | Documentos de Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- <entryPointsCollection> element
- application manifests [Office development in Visual Studio], <entryPointsCollection> element
- entryPointsCollection element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 357e2b4d7aedb82b63676055f1ad1215171a25cf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ltentrypointscollectiongt-element-office-development-in-visual-studio"></a>&lt;entryPointsCollection&gt; elemento (desarrollo de Office en Visual Studio)
  El elemento `entryPointsCollection` del espacio de nombres `vstav3` contiene todos los elementos `entryPoints` asociados a soluciones de Office.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<entryPointsCollection>  
  <entryPoints>  
    <entryPoint>  
    </entryPoint>  
    <entryPoint>  
    </entryPoint>  
    <entryPoint>  
    </entryPoint>  
  </entryPoints>  
</entryPointsCollection>  
```  
  
## <a name="elements-and-attributes"></a>Elementos y atributos  
 El elemento `entryPointsCollection` es obligatorio y se encuentra en el espacio de nombres `vstav3` . Los elementos secundarios también deben estar en este espacio de nombres. Solo hay un elemento `entryPointsCollection` definido en un manifiesto de la aplicación.  
  
 El elemento `entryPointsCollection` no tiene atributos.  
  
 `entryPointsCollection` tiene los siguientes elementos.  
  
### <a name="entrypoints"></a>entryPoints  
 Requerido. El rol de la `entryPoints` elemento en el `vstav3` espacio de nombres se define en [ &#60;entryPoints&#62; elemento &#40;desarrollo de Office en Visual Studio&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md).  
  
## <a name="document-level-customization-example"></a>Ejemplo de personalización de nivel de documento  
  
### <a name="description"></a>Descripción  
 En el siguiente ejemplo de código, se muestra el elemento `entryPointsCollection` en un manifiesto de aplicación para una solución de nivel de documento implementada mediante [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Código  
  
```  
<vstav3:entryPointsCollection>  
    <vstav3:entryPoints>  
      <vstav3:entryPoint   
        class="ContosoExcelWorkbook.ThisWorkbook">  
        <assemblyIdentity   
          name="ContosoExcelWorkbook"   
          version="1.0.0.0"   
          language="neutral"   
          processorArchitecture="msil" />  
      </vstav3:entryPoint>  
      <vstav3:entryPoint   
        class="ContosoExcelWorkbook.Sheet1">  
        <assemblyIdentity   
          name="ContosoExcelWorkbook"   
          version="1.0.0.0"   
          language="neutral"   
          processorArchitecture="msil" />  
      </vstav3:entryPoint>  
      <vstav3:entryPoint   
        class="ContosoExcelWorkbook.Sheet2">  
        <assemblyIdentity   
          name="ContosoExcelWorkbook"   
          version="1.0.0.0"   
          language="neutral"   
          processorArchitecture="msil" />  
      </vstav3:entryPoint>  
      <vstav3:entryPoint   
        class="ContosoExcelWorkbook.Sheet3">  
        <assemblyIdentity   
          name="ContosoExcelWorkbook"   
          version="1.0.0.0"   
          language="neutral"   
          processorArchitecture="msil" />  
      </vstav3:entryPoint>  
    </vstav3:entryPoints>  
  </vstav3:entryPointsCollection>  
```  
  
## <a name="vsto-add-in-example"></a>Ejemplo de complemento de VSTO  
  
### <a name="description"></a>Descripción  
 En el ejemplo de código siguiente se muestra un elemento `entryPointsCollection` en un manifiesto de aplicación para una solución de nivel de aplicación implementada mediante [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Código  
  
```  
<vstav3:entryPointsCollection>  
    <vstav3:entryPoints>  
      <vstav3:entryPoint   
        class="ContosoOutlookAddIn.ThisAddIn">  
        <assemblyIdentity   
          name="ContosoOutlookAddIn"   
          version="1.0.0.0"   
          language="neutral"   
          processorArchitecture="msil" />  
      </vstav3:entryPoint>  
    </vstav3:entryPoints>  
  </vstav3:entryPointsCollection>  
```  
  
## <a name="multi-project-deployment-example"></a>Ejemplo de implementación de varios proyectos  
  
### <a name="description"></a>Descripción  
 En el ejemplo de código siguiente se muestra un elemento `entryPointsCollection` de un manifiesto de aplicación para una implementación de varios proyectos con dos soluciones de Office. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Código  
  
```  
<vstav3:entryPointsCollection>  
      <vstav3:entryPoints   
        id="ContosoExcel">  
        <vstav3:entryPoint   
          class="ContosoExcelWorkbook.ThisWorkbook">  
          <assemblyIdentity   
            name="ContosoExcelWorkbook"   
            version="1.0.0.0"   
            language="neutral"   
            processorArchitecture="msil" />  
        </vstav3:entryPoint>  
        <vstav3:entryPoint   
          class="ContosoExcelWorkbook.Sheet1">  
          <assemblyIdentity   
            name="ContosoExcelWorkbook"   
            version="1.0.0.0"   
            language="neutral"   
            processorArchitecture="msil" />  
        </vstav3:entryPoint>  
        <vstav3:entryPoint   
          class="ContosoExcelWorkbook.Sheet2">  
          <assemblyIdentity   
            name="ContosoExcelWorkbook"   
            version="1.0.0.0"   
            language="neutral"   
            processorArchitecture="msil" />  
        </vstav3:entryPoint>  
        <vstav3:entryPoint   
          class="ContosoExcelWorkbook.Sheet3">  
          <assemblyIdentity   
            name="ContosoExcelWorkbook"   
            version="1.0.0.0"   
            language="neutral"   
            processorArchitecture="msil" />  
        </vstav3:entryPoint>  
      </vstav3:entryPoints>  
      <vstav3:entryPoints   
        id="ContosoOutlook">  
        <vstav3:entryPoint   
          class="ContosoOutlookAddIn.ThisAddIn">  
          <assemblyIdentity   
            name="ContosoOutlookAddIn"   
            version="1.0.0.0"   
            language="neutral"   
            processorArchitecture="msil" />  
        </vstav3:entryPoint>  
      </vstav3:entryPoints>  
    </vstav3:entryPointsCollection>  
```  
  
## <a name="see-also"></a>Vea también  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifiesto de aplicación ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  