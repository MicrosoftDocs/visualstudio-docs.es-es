---
title: Uso de Microsoft.VisualStudio.TestTools.UnitTesting en pruebas unitarias
ms.date: 03/02/2018
ms.topic: reference
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: ae7cbddb3ea7d7f94b23d723f6641a95dd28ed40
ms.sourcegitcommit: 51dad3e11d7580567673e0d426ab3b0a17584319
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/10/2019
ms.locfileid: "66820343"
---
# <a name="use-the-mstest-framework-in-unit-tests"></a>Usar el marco de trabajo MSTest en pruebas unitarias

El marco de trabajo [MSTest](<xref:Microsoft.VisualStudio.TestTools.UnitTesting>) admite pruebas unitarias en Visual Studio. Utilice las clases y los miembros en el espacio de nombres <xref:Microsoft.VisualStudio.TestTools.UnitTesting> cuando se estén codificando pruebas unitarias. También puede utilizarlos si está perfeccionando una prueba unitaria que se generó a partir de código.

## <a name="framework-members"></a>Miembros del marco de trabajo

Con el fin de proporcionar una visión general más clara del marco de pruebas unitarias, esta sección organiza los miembros del espacio de nombres <xref:Microsoft.VisualStudio.TestTools.UnitTesting> en grupos de funcionalidad relacionada.

> [!NOTE]
> Los elementos de atributo, cuyos nombres terminan con "Attribute", se pueden utilizar con o sin "Attribute" al final. Por ejemplo, los dos siguientes ejemplos de código funcionan de forma idéntica:
>
> `[TestClass()]`
>
> `[TestClassAttribute()]`

### <a name="members-used-for-data-driven-testing"></a>Miembros utilizados para pruebas controladas por datos

Utilice los siguientes elementos para configurar pruebas unitarias controladas por datos. Para obtener más información, vea [Cómo: Crear una prueba unitaria controlada por datos](../test/how-to-create-a-data-driven-unit-test.md) y [Tutorial: Utilizar un archivo de configuración para definir un origen de datos](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataAccessMethod>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElement>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElementCollection>

## <a name="attributes-used-to-establish-a-calling-order"></a>Atributos utilizados para establecer un orden de llamada

Un elemento de código representativo con uno de los siguientes atributos se llama en el momento que especifique. Para obtener más información, vea [Estructura de una prueba unitaria](https://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144).

### <a name="attributes-for-assemblies"></a>Atributos para ensamblados

Se llama a AssemblyInitialize y AssemblyCleanup inmediatamente después de que se carga el ensamblado e inmediatamente antes de que se descargue.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyCleanupAttribute>

### <a name="attributes-for-classes"></a>Atributos para clases

Se llaman a ClassInitialize y ClassCleanup inmediatamente después de que se cargue la clase e inmediatamente antes de que se descargue.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassCleanupAttribute>

### <a name="attributes-for-test-methods"></a>Atributos a los métodos de prueba

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute>

## <a name="attributes-used-to-identify-test-classes-and-methods"></a>Atributos utilizados para identificar clases y métodos de prueba

Cada clase de prueba debe tener el atributo `TestClass` y todos los métodos de prueba deben tener el atributo `TestMethod`. Para obtener más información, vea [Estructura de una prueba unitaria](https://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute>

## <a name="assert-classes-and-related-exceptions"></a>Clases Assert y excepciones relacionadas

Las pruebas unitarias pueden comprobar el comportamiento de aplicaciones concretas por su uso de varias clases de aserciones, excepciones y atributos. Para obtener más información, vea [Usar las clases Assert](../test/using-the-assert-classes.md).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>

## <a name="the-testcontext-class"></a>La clase TestContext

Los siguientes atributos y los valores asignados a ellos aparecen en la ventana Propiedades de Visual Studio para un método de prueba determinado. Estos atributos no están diseñados para tener acceso a través del código de la prueba unitaria. En su lugar, afectan a las formas en que se usa o ejecuta la prueba unitaria, ya sea a través del IDE de Visual Studio, o por el motor de pruebas de Visual Studio. Por ejemplo, algunos de estos atributos aparecen como columnas en las ventanas **Administrador de pruebas** y **Resultados de pruebas**, lo que significa que puede usarlas para agrupar y ordenar las pruebas y resultados de pruebas. Uno de estos atributos es <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>, que se utiliza para agregar metadatos arbitrarios a las pruebas unitarias. Por ejemplo, se puede utilizar para almacenar el nombre de una prueba superada que cubre esta prueba, marcando la prueba unitaria con `[TestProperty("TestPass", "Accessibility")]`. O se puede utilizar para almacenar un indicador del tipo de prueba que es con `[TestProperty("TestKind", "Localization")]`. La propiedad que se crea mediante este atributo y el valor de propiedad que se asigna se muestran en la ventana **Propiedades** de Visual Studio bajo el encabezado **Específico de prueba**.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DeploymentItemAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DescriptionAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.IgnoreAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.WorkItemAttribute>

## <a name="test-configuration-classes"></a>Clases de configuración de prueba

- <xref:Microsoft.TeamFoundation.TestManagement.Client.ObjectTypes>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection>

## <a name="attributes-used-to-generate-reports"></a>Atributos que se utilizan para generar informes

Los atributos de esta sección relacionan el método de prueba que decoran con entidades de la jerarquía del proyecto de un proyecto de equipo de Team Foundation Server.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssIterationAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssProjectStructureAttribute>

## <a name="classes-used-with-private-accessors"></a>Clases utilizadas con descriptores de acceso privados

Puede generar una prueba unitaria para un método privado. Esta generación crea una clase de descriptor de acceso privado, que crea una instancia de un objeto de la clase <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject>. La clase <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject> es una clase contenedora que utiliza la reflexión como parte del proceso de descriptor de acceso privado. La clase <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateType> es similar, pero se utiliza para llamar a métodos estáticos privados en lugar de llamar a métodos de instancia privados.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateType>

## <a name="see-also"></a>Vea también

- Documentación de referencia de <xref:Microsoft.VisualStudio.TestTools.UnitTesting>
