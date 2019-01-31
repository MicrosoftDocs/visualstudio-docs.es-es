---
title: Usar miembros de Microsoft.VisualStudio.TestTools.UnitTesting en pruebas unitarias | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 0fa335fd-e442-448f-913f-25a19df90a93
caps.latest.revision: 8
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c3b0e7cf2ddc4ada4fe015feba17c5adbcc328d3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54803272"
---
# <a name="using-microsoftvisualstudiotesttoolsunittesting-members-in-unit-tests"></a>Usar miembros de Microsoft.VisualStudio.TestTools.UnitTesting en pruebas unitarias
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
El marco de pruebas unitarias es compatible con pruebas unitarias en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Utilice las clases y los miembros en el espacio de nombres <xref:Microsoft.VisualStudio.TestTools.UnitTesting> cuando se estén codificando pruebas unitarias. Se pueden utilizar cuando haya escrito la unidad de prueba desde el principio o si está adaptando una prueba unitaria que se generó a partir de código que se está probando.

## <a name="groups-of-elements"></a>Grupo de elementos
 Con el fin de proporcionar una visión general más clara del marco de pruebas unitarias, esta sección organiza los elementos del espacio de nombres UnitTesting en grupos de funcionalidades relacionadas.

> [!NOTE]
> Los elementos de atributo, cuyos nombres terminan en la cadena Attribute, se pueden utilizar con o sin la cadena Attribute. Por ejemplo, los dos siguientes ejemplos de código funcionan de forma idéntica:
>
>  `[TestClass()]`
>
>  `[TestClassAttribute()]`

### <a name="elements-used-for-data-driven-testing"></a>Elementos utilizados para pruebas controladas por datos
 Utilice los siguientes elementos para configurar pruebas unitarias controladas por datos. Para obtener más información, vea el tema sobre [cómo Crear una prueba unitaria controlada por datos](../test/how-to-create-a-data-driven-unit-test.md) y [Tutorial: Uso de un archivo de configuración para definir un origen de datos](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md)

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataAccessMethod>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElement>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElementCollection>

## <a name="attributes-used-to-establish-a-calling-order"></a>Atributos utilizados para establecer un orden de llamada
 Un elemento de código representativo con uno de los siguientes atributos se llama en el momento que especifique. Para obtener más información, consulte [Estructura de una prueba unitaria](http://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144).

### <a name="for-assemblies"></a>Para los ensamblados
 Se llama a AssemblyInitialize y AssemblyCleanup inmediatamente después de que se carga el ensamblado e inmediatamente antes de que se descargue.

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyInitializeAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyCleanupAttribute>

### <a name="for-classes"></a>Para las clases
 Se llaman a ClassInitialize y ClassCleanup inmediatamente después de que se cargue la clase e inmediatamente antes de que se descargue.

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassInitializeAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassCleanupAttribute>

### <a name="for-test-methods"></a>Para los métodos de prueba

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute>

## <a name="attributes-used-to-identify-test-classes-and-methods"></a>Atributos utilizados para identificar clases y métodos de prueba
 Cada clase de prueba debe tener el atributo TestClass y todos los métodos de prueba deben tener el atributo TestMethod. Para obtener más información, consulte [Estructura de una prueba unitaria](http://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144).

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute>

## <a name="assert-classes-and-related-exceptions"></a>Clases Assert y excepciones relacionadas
 Las pruebas unitarias pueden comprobar el comportamiento de aplicaciones concretas por su uso de varias clases de instrucciones Assert, excepciones y atributos. Para obtener más información, consulte [Usar las clases Assert](../test/using-the-assert-classes.md).

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute>

## <a name="the-testcontext-class"></a>La clase TestContext
 Los siguientes atributos y los valores asignados a ellos aparecen en la ventana Propiedades de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para un método de prueba determinado. Estos atributos no están diseñados para tener acceso a través del código de la prueba unitaria. En su lugar, afectan a las formas en que se usa o ejecuta la prueba unitaria, ya sea a través del IDE de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], o por el motor de pruebas [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Por ejemplo, algunos de estos atributos aparecen como columnas en las ventanas Administrador de pruebas y Resultados de pruebas, lo que significa que puede usarlas para agrupar y ordenar las pruebas y resultados de pruebas. Uno de estos atributos es TestPropertyAttribute, que se utiliza para agregar metadatos arbitrarios a las pruebas unitarias. Por ejemplo, se puede utilizar para almacenar el nombre de una prueba superada que cubre esta prueba, marcando la prueba unitaria con `[TestProperty("TestPass", "Accessibility")]`. O se puede utilizar para almacenar un indicador del tipo de prueba que es: `[TestProperty("TestKind", "Localization")]`. La propiedad que se crea mediante este atributo y el valor de propiedad que se asigna, se muestran en la ventana Propiedades de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bajo el encabezado **Específico de prueba**.

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DeploymentItemAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DescriptionAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.IgnoreAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.WorkItemAttribute>

## <a name="test-configuration-classes"></a>Clases de configuración de prueba

-   <xref:Microsoft.TeamFoundation.TestManagement.Client.ObjectTypes>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection>

## <a name="attributes-used-for-generating-reports"></a>Atributos utilizados para la generación de informes
 Los atributos de esta sección relacionan el método de prueba que decoran con entidades de la jerarquía del proyecto de un proyecto de equipo de [!INCLUDE[esprtfs](../includes/esprtfs-md.md)].

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssIterationAttribute>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssProjectStructureAttribute>

## <a name="classes-used-with-private-accessors"></a>Clases utilizadas con descriptores de acceso privados
 Como se describe en [Usar Publicize para crear un descriptor de acceso privado](http://msdn.microsoft.com/2056c6a7-6672-42a7-8f53-fead33c56deb), puede generar una prueba unitaria para un método privado. Esta generación crea una clase de descriptor de acceso privado, que crea una instancia de un objeto de la clase PrivateObject. La clase PrivateObject es una clase contenedora que utiliza la reflexión como parte del proceso de descriptor de acceso privado. La clase PrivateType es similar, pero se utiliza para llamar a métodos estáticos privados en lugar de llamar a métodos de instancia privados.

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject>

-   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateType>

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting>