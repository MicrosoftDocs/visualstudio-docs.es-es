---
title: Crear proyectos personalizados con identificación de versión | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5233d3ff-6e89-4401-b449-51b4686becca
caps.latest.revision: 33
manager: douge
ms.openlocfilehash: 038f478d6a8dbdd3dc050b6db85af82be377c325
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49833010"
---
# <a name="making-custom-projects-version-aware"></a>Crear proyectos personalizados con identificación de versión
En un sistema de proyecto personalizado, puede permitir que los proyectos de ese tipo se carguen en varias versiones de Visual Studio. También puede evitar que los proyectos de ese tipo se carguen en una versión anterior de Visual Studio. Además, puede permitir que ese proyecto se identifique en una versión posterior en caso de que el proyecto necesite reparación, conversión o degradación.  
  
## <a name="allowing-projects-to-load-in-multiple-versions"></a>Permitir cargar proyectos en varias versiones  
 Puede modificar la mayoría de los proyectos que se crearon en [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] con SP1 o posterior para que funcionen en varias versiones.  
  
 Antes de cargar un proyecto, Visual Studio llama al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly%2A> para determinar si se puede actualizar el proyecto. Si el proyecto se puede actualizar, el método `UpgradeProject_CheckOnly` establece una marca que provoca una llamada posterior al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> para actualizar el proyecto. Dado que no se pueden actualizar proyectos incompatibles, `UpgradeProject_CheckOnly` comprueba primero la compatibilidad del proyecto, como se describe en la sección anterior.  
  
 Como autor de un sistema de proyecto, implemente `UpgradeProject_CheckOnly` (desde la interfaz `IVsProjectUpgradeViaFactory4` ) para proporcionar a los usuarios de su sistema de proyecto una comprobación de actualizaciones. Cuando los usuarios abren un proyecto, se llama a este método para determinar si un proyecto se debe reparar antes de cargarse. Los posibles requisitos de actualización se enumeran en `VSPUVF_REPAIRFLAGS`, e incluyen las siguientes posibilidades:  
  
1.  `SPUVF_PROJECT_NOREPAIR`: no necesita ninguna reparación.  
  
2.  `VSPUVF_PROJECT_SAFEREPAIR`: hace que el proyecto sea compatible con una versión anterior sin los problemas que pueda haber encontrado con las versiones anteriores del producto.  
  
3.  `VSPUVF_PROJECT_UNSAFEREPAIR`: hace que el proyecto sea compatible con versiones anteriores, pero con algún riesgo de que se produzcan los problemas que pueda haber encontrado con las versiones anteriores del producto. Por ejemplo, el proyecto no será compatible si dependía de distintas versiones de SDK.  
  
4.  `VSPUVF_PROJECT_ONEWAYUPGRADE`: hace que el proyecto sea incompatible con una versión anterior.  
  
5.  `VSPUVF_PROJECT_INCOMPATIBLE`: indica que la versión actual no es compatible con este proyecto.  
  
6.  `VSPUVF_PROJECT_DEPRECATED`: indica que ya no se admite este proyecto.  
  
> [!NOTE]
>  Para evitar confusiones, no combine marcas de actualización cuando las establezca. Por ejemplo, no cree un estado de actualización ambiguo como `VSPUVF_PROJECT_SAFEREPAIR | VSPUVF_PROJECT_DEPRECATED`.  
  
 Los tipos de proyecto pueden implementar la función `UpgradeProjectFlavor_CheckOnly` desde la interfaz `IVsProjectFlavorUpgradeViaFactory2` . Para usar esta función, la implementación de `IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly` que se ha mencionado anteriormente debe llamarla. Esta llamada ya se ha implementado en el sistema de proyectos base de Visual Basic o C#. El efecto de esta función permite que los tipos de proyecto puedan determinar también los requisitos de actualización de un proyecto, además de lo que ha determinado el sistema de proyecto base. El cuadro de diálogo de compatibilidad muestra el más grave de los dos requisitos.  
  
 Cuando Visual Studio realiza una comprobación de actualizaciones, proporciona un registrador en lugar de un valor NULL como en versiones anteriores de Visual Studio. El registrador permite a los sistemas y tipos de proyecto proporcionar información adicional que le ayudará a comprender la naturaleza de los cambios necesarios para que sus proyectos más antiguos se carguen correctamente. Se recomienda usar el registrador para proporcionar más información en lugar de los cuadros de diálogo. Para obtener más información, vea [The Upgrade Logger](../misc/making-custom-projects-version-aware.md#BKMK_UpgradeLogger) , más adelante en este tema.  
  
 Para las implementaciones administradas, las interfaces de actualización de proyectos están disponibles en el ensamblado de interoperabilidad Microsoft.VisualStudio.Shell.Interop.11.0.dll.  
  
 El método `UpgradeProject` puede determinar si los cambios que realiza impedirán que el proyecto se cargue en una versión anterior de Visual Studio. Si es así, el método marca el proyecto como incompatible. Para entender cómo un proyecto se marca como incompatible, vea [Marking a Project as Incompatible](../misc/making-custom-projects-version-aware.md#BKMK_Incompat) anteriormente en este tema. Se recomienda que, después de que aparezca este cuadro de diálogo, marque el proyecto como incompatible llamando al método `IVsAppCompat.BreakAssetCompatibility` directamente, en lugar de llamar primero al método `IVsAppCompat.AskForUserConsentToBreakAssetCompat` porque no es necesario que el cuadro de diálogo aparezca dos veces.  
  
 Este es un ejemplo que ayuda a resumir la experiencia de usuario de compatibilidad. Si un proyecto se creó en una versión anterior y la versión actual determina que es necesaria una actualización, Visual Studio muestra un cuadro de diálogo para pedir permiso al usuario para realizar los cambios. Si el usuario acepta, se modifica el proyecto y, a continuación, se carga. Si luego se cierra la solución y se vuelve a abrir en la versión anterior, el proyecto actualizado de forma unidireccional será incompatible y no se cargará. Si el proyecto solo requería una reparación (en lugar de una actualización), el proyecto reparado se abrirá en ambas versiones.  
  
##  <a name="BKMK_Incompat"></a> Marcar un proyecto como Incompatible  
 Puede marcar un proyecto como incompatible con versiones anteriores de Visual Studio.  Por ejemplo, suponga que crea un proyecto que usa una característica de .NET Framework 4.5. Dado que este proyecto no se puede compilar en [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)], puede marcarlo como incompatible para impedir que esa versión intente cargarlo.  
  
 El componente que agrega la característica incompatible es responsable de marcar el proyecto como incompatible. El componente debe tener acceso a la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> que representa los proyectos de interés.  
  
#### <a name="to-mark-a-project-as-incompatible"></a>Para marcar un proyecto como incompatible  
  
1.  En el componente, obtenga una interfaz `IVsAppCompat` del servicio global SVsSolution.  
  
     Para obtener más información, consulta <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>.  
  
2.  En el componente, llame a `IVsAppCompat.AskForUserConsentToBreakAssetCompat`, y pásele una matriz de interfaces `IVsHierarchy` que representan los proyectos de interés.  
  
     Este método tiene la siguiente firma:  
  
    ```  
    HRESULT AskForUserConsentToBreakAssetCompat([in] SAFEARRAY(IVsHierarchy*) sarrProjectHierarchies)  
  
    ```  
  
     Si implementa este código, aparecerá un cuadro de diálogo de compatibilidad del proyecto. En el cuadro de diálogo se pide permiso al usuario para marcar todos los proyectos especificados como incompatibles. Si el usuario acepta, `AskForUserConsentToBreakAssetCompat` devuelve `S_OK`; en caso contrario, `AskForUserConsentToBreakAssetCompat` devuelve `OLE_E_PROMPTSAVECANCELLED`.  
  
    > [!WARNING]
    >  En los escenarios más habituales, la matriz `IVsHierarchy` contendrá un único elemento.  
  
3.  Si `AskForUserConsentToBreakAssetCompat` devuelve `S_OK`, el componente realiza o acepta los cambios que interrumpen la compatibilidad.  
  
4.  En el componente, llame al método `IVsAppCompat.BreakAssetCompatibility` para cada proyecto que quiera marcar como incompatible. El componente puede establecer el valor del parámetro `lpszMinimumVersion` en una versión mínima específica en lugar de que Visual Studio busque la cadena de versión actual en el registro. Este enfoque minimiza el riesgo de que el componente establezca inadvertidamente un valor superior en el futuro, en función de lo que haya en el registro en ese momento. Si se estableciera ese valor superior, Visual Studio no podría abrir el proyecto.  
  
     Este método tiene la siguiente firma:  
  
    ```  
    HRESULT BreakAssetCompatibility([in] IVsHierarchy * pProjHier), [in] LPCOLESTR lpszMinimumVersion);  
  
    ```  
  
     Si el componente establece `lpszMinimumVersion` en NULL, el método `BreakAssetCompatibility` llama al método `IVsAppCompat.GetCurrentDesignTimeCompatVersion` para obtener una cadena que represente la versión actual de Visual Studio.  
  
     Este método tiene la siguiente firma:  
  
    ```  
    HRESULT GetCurrentDesignTimeCompatVersion([out] BSTR * pbstrCurrentDesignTimeCompatVersion)  
    ```  
  
     A continuación, el método BreakAssetCompatibility llama al método `IVsHierarchy.SetProperty` para establecer la propiedad `VSHPROPID_MinimumDesignTimeCompatVersion` raíz en el valor de la cadena de versión que obtuvo en el paso anterior.  
  
     Para obtener más información, consulta <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A>.  
  
> [!IMPORTANT]
>  Debe implementar la propiedad `VSHPROPID_MinimumDesignTimeCompatVersion` para marcar un proyecto como compatible o incompatible. Por ejemplo, si el sistema de proyectos usa un archivo de proyecto MSBuild, agregue al archivo de proyecto una propiedad de compilación `<MinimumVisualStudioVersion>` que tenga un valor igual al valor de propiedad `VSHPROPID_MinimumDesignTimeCompatVersion` correspondiente.  
  
## <a name="detecting-whether-a-project-is-incompatible"></a>Detectar si un proyecto es incompatible  
 Debe impedirse que se cargue un proyecto incompatible con la versión actual de Visual Studio. Además, un proyecto incompatible no se puede cargar ni reparar. Por lo tanto, la compatibilidad de un proyecto se debe comprobar dos veces: la primera, cuando se está considerando para actualización o reparación y la segunda, antes de que se cargue.  
  
 Para habilitar la detección de incompatibilidad de proyectos, debe implementar los métodos <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>. Si un proyecto es incompatible, `UpgradeProject_CheckOnly` debe devolver el código de correcto `VS_S_INCOMPATIBLEPROJECT`y `CreateProject` debe devolver el código de error `VS_E_INCOMPATIBLEPROJECT`. Para los proyectos con tipo, debe implementar `IVsProjectFlavorUpgradeViaFactory2.UpgradeProjectFlavor_CheckOnly` en lugar de `IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly`.  
  
 Un sistema de proyecto con tipo es el que tiene un tipo de proyecto web, Office (VSTO), Silverlight u otro creado sobre él. Los sistemas de proyectos anteriores que ya implementan `IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly` y los sistemas de proyectos con tipo que ya implementan `IVsProjectFlavorUpgradeViaFactory.UpgradeProjectFlavor_CheckOnly` siguen siendo compatibles. La versión anterior de `IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly` tiene la siguiente firma de implementación:  
  
```  
IVsProjectUpgradeViaFactory::UpgradeProject_CheckOnly(  
  
/* [in] */ BSTR bstrFileName,  
/* [in] */ IVsUpgradeLogger *pLogger,  
/* [out] */ BOOL *pUpgradeRequired,  
/* [out] */ GUID *pguidNewProjectFactory,  
/* [out] */ VSPUVF_FLAGS *pUpgradeProjectCapabilityFlags  
)  
```  
  
 Si este método establece `pUpgradeRequired` en TRUE y devuelve `S_OK`, el resultado se trata como "Actualización" y como si el método hubiera establecido una marca de actualización en el valor `VSPUVF_PROJECT_ONEWAYUPGRADE`, que se describe más adelante en este tema. Los siguientes valores devueltos son compatibles usando este método anterior, pero solo cuando `pUpgradeRequired` se establece en TRUE:  
  
1. `VS_S_PROJECT_SAFEREPAIRREQUIRED`. Este valor devuelto convierte el valor de `pUpgradeRequired` en TRUE como equivalente a `VSPUVF_PROJECT_SAFEREPAIR`, que se describe más adelante en este tema.  
  
2. `VS_S_PROJECT_UNSAFEREPAIRREQUIRED`. Este valor devuelto convierte el valor de `pUpgradeRequired` en TRUE como equivalente a `VSPUVF_PROJECT_UNSAFEREPAIR`, que se describe más adelante en este tema.  
  
3. `VS_S_PROJECT_ONEWAYUPGRADEREQUIRED`. Este valor devuelto convierte el valor de `pUpgradeRequired` en TRUE como equivalente a `VSPUVF_PROJECT_ONEWAYUPGRADE`, que se describe más adelante en este tema.  
  
   Las nuevas implementaciones en `IVsProjectUpgradeViaFactory4` y `IVsProjectFlavorUpgradeViaFactory2` permiten especificar el tipo de migración con más precisión.  
  
> [!NOTE]
>  Puede almacenar en caché el resultado de la comprobación de compatibilidad mediante el método `UpgradeProject_CheckOnly` para que se pueda usar también por la llamada subsiguiente a `CreateProject`.  
  
 Por ejemplo, si los métodos `UpgradeProject_CheckOnly` y `CreateProject` que están escritos para un sistema de proyectos [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] con SP1 examinan un archivo de proyecto y observan que la propiedad de compilación `<MinimumVisualStudioVersion>` es "11.0", Visual Studio 2010 con SP1 no cargará el proyecto. Además, el **navegador de soluciones** indicará que el proyecto es "incompatible" y no lo cargará.  
  
##  <a name="BKMK_UpgradeLogger"></a> El registrador de actualización  
 La llamada a `IVsProjectUpgradeViaFactory::UpgradeProject` contiene un registrador `IVsUpgradeLogger` , que los sistemas de proyectos y tipos deben usar para proporcionar el seguimiento detallado de las actualizaciones para la solución de problemas. Si se registra una advertencia o un error, Visual Studio muestra el informe de actualización.  
  
 Cuando escriba en el registrador de actualizaciones, tenga en cuenta las siguientes directrices:  
  
-   Visual Studio llamará al método Flush una vez haya finalizado la actualización de todos los proyectos. No lo llame en el sistema de proyecto.  
  
-   La función LogMessage tiene los siguientes niveles de error:  
  
    -   0 es cualquier información de la que le gustaría hacer un seguimiento.  
  
    -   1 es una advertencia.  
  
    -   2 es un error.  
  
    -   3 es el formateador de informes. Cuando se actualiza el proyecto, registre la palabra "Converted" una vez y no la localice.  
  
-   Si un proyecto no necesita reparación ni actualización, Visual Studio generará el archivo de registro solo si el sistema de proyecto ha registrado una advertencia o un error durante los métodos UpgradeProject_CheckOnly o UpgradeProjectFlavor_CheckOnly.