---
title: Usar miembros de Microsoft.VisualStudio.TestTools.UnitTesting en pruebas unitarias | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 3e0be7d788d4471f249b50f8c846343514b1c346
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="using-microsoftvisualstudiotesttoolsunittesting-members-in-unit-tests"></a>Usar miembros de Microsoft.VisualStudio.TestTools.UnitTesting en pruebas unitarias
El marco de pruebas unitarias es compatible con pruebas unitarias en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Use las clases y los miembros del espacio de nombres Microsoft.VisualStudio.TestPlatform.UnitTestFramework> cuando codifique pruebas unitarias. Se pueden utilizar cuando haya escrito la unidad de prueba desde el principio o si está adaptando una prueba unitaria que se generó a partir de código que se está probando.  
  
## <a name="groups-of-elements"></a>Grupo de elementos  
 Con el fin de proporcionar una visión general más clara del marco de pruebas unitarias, esta sección organiza los elementos del espacio de nombres UnitTesting en grupos de funcionalidades relacionadas.  
  
> [!NOTE]
>  Los elementos de atributo, cuyos nombres terminan en la cadena Attribute, se pueden utilizar con o sin la cadena Attribute. Por ejemplo, los dos siguientes ejemplos de código funcionan de forma idéntica:  
>   
>  `[TestClass()]`  
>   
>  `[TestClassAttribute()]`  
  
### <a name="elements-used-for-data-driven-testing"></a>Elementos utilizados para pruebas controladas por datos  
 Utilice los siguientes elementos para configurar pruebas unitarias controladas por datos. Para obtener más información, consulte [Cómo: Crear una prueba unitaria controlada por datos](../test/how-to-create-a-data-driven-unit-test.md) y [Tutorial: usar un archivo de configuración para definir un origen de datos](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md).  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataAccessMethod  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataSourceAttribute 
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataSourceElement  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataSourceElementCollection  
  
## <a name="attributes-used-to-establish-a-calling-order"></a>Atributos utilizados para establecer un orden de llamada

Un elemento de código representativo con uno de los siguientes atributos se llama en el momento que especifique. Para obtener más información, consulte [Estructura de una prueba unitaria](http://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144).

### <a name="for-assemblies"></a>Para los ensamblados  
 Se llama a AssemblyInitialize y AssemblyCleanup inmediatamente después de que se carga el ensamblado e inmediatamente antes de que se descargue.  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssemblyInitializeAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssemblyCleanupAttribute  
  
### <a name="for-classes"></a>Para las clases  
 Se llaman a ClassInitialize y ClassCleanup inmediatamente después de que se cargue la clase e inmediatamente antes de que se descargue.  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.ClassInitializeAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.ClassCleanupAttribute  
  
### <a name="for-test-methods"></a>Para los métodos de prueba  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestInitializeAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestCleanupAttribute  
  
## <a name="attributes-used-to-identify-test-classes-and-methods"></a>Atributos utilizados para identificar clases y métodos de prueba

Cada clase de prueba debe tener el atributo TestClass y todos los métodos de prueba deben tener el atributo TestMethod. Para obtener más información, consulte [Estructura de una prueba unitaria](http://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144).
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestClassAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestMethodAttribute  
  
## <a name="assert-classes-and-related-exceptions"></a>Clases Assert y excepciones relacionadas  
 Las pruebas unitarias pueden comprobar el comportamiento de aplicaciones concretas por su uso de varias clases de instrucciones Assert, excepciones y atributos. Para obtener más información, consulte [Usar las clases Assert](../test/using-the-assert-classes.md).  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.Assert 
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.CollectionAssert  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.StringAssert  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssertFailedException  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssertInconclusiveException  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.UnitTestAssertException  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.ExpectedExceptionAttribute  
  
## <a name="the-testcontext-class"></a>La clase TestContext  
 Los siguientes atributos y los valores asignados a ellos aparecen en la ventana Propiedades de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para un método de prueba determinado. Estos atributos no están diseñados para tener acceso a través del código de la prueba unitaria. En su lugar, afectan a las formas en que se usa o ejecuta la prueba unitaria, ya sea a través del IDE de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], o por el motor de pruebas [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Por ejemplo, algunos de estos atributos aparecen como columnas en las ventanas Administrador de pruebas y Resultados de pruebas, lo que significa que puede usarlas para agrupar y ordenar las pruebas y resultados de pruebas. Uno de estos atributos es TestPropertyAttribute, que se utiliza para agregar metadatos arbitrarios a las pruebas unitarias. Por ejemplo, se puede utilizar para almacenar el nombre de una prueba superada que cubre esta prueba, marcando la prueba unitaria con `[TestProperty("TestPass", "Accessibility")]`. O se puede utilizar para almacenar un indicador del tipo de prueba que es: `[TestProperty("TestKind", "Localization")]`. La propiedad que se crea mediante este atributo y el valor de propiedad que se asigna, se muestran en la ventana Propiedades de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bajo el encabezado **Específico de prueba**.  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.OwnerAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DeploymentItemAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DescriptionAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.HostTypeAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.IgnoreAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.PriorityAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestPropertyAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.WorkItemAttribute  
  
## <a name="test-configuration-classes"></a>Clases de configuración de prueba  
  
-   Microsoft.TeamFoundation.TestManagement.Client.ObjectTypes>  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestConfigurationSection  
  
## <a name="attributes-used-for-generating-reports"></a>Atributos utilizados para la generación de informes  
 Los atributos de esta sección relacionan el método de prueba que decoran con entidades de la jerarquía del proyecto de un proyecto de equipo de [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)].  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.CssIterationAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.CssProjectStructureAttribute  
  
## <a name="classes-used-with-private-accessors"></a>Clases utilizadas con descriptores de acceso privados

Puede generar una prueba unitaria para un método privado. Esta generación crea una clase de descriptor de acceso privado, que crea una instancia de un objeto de la clase PrivateObject. La clase PrivateObject es una clase contenedora que utiliza la reflexión como parte del proceso de descriptor de acceso privado. La clase PrivateType es similar, pero se utiliza para llamar a métodos estáticos privados en lugar de llamar a métodos de instancia privados.

- Microsoft.VisualStudio.TestPlatform.UnitTestFramework.PrivateObject

- Microsoft.VisualStudio.TestPlatform.UnitTestFramework.PrivateType
