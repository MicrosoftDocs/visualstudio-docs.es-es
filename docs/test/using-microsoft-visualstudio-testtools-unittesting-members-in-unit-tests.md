---
title: "Usar miembros de Microsoft.VisualStudio.TestTools.UnitTesting en pruebas unitarias | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0fa335fd-e442-448f-913f-25a19df90a93
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "mlearned"
manager: "douge"
---
# Usar miembros de Microsoft.VisualStudio.TestTools.UnitTesting en pruebas unitarias
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El marco de pruebas unitarias admite las pruebas unitarias en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Utilice las clases y los miembros del espacio de nombres <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework> cuando codifique pruebas unitarias.  Puede utilizarlas cuando escriba la prueba unitaria desde cero o si está adaptando una que generó a partir del código que está probando.  
  
## Grupos de elementos  
 Para ayudar a proporcionar información general más clara del marco de pruebas unitarias, en esta sección se organizan los elementos del espacio de nombres UnitTesting en grupos de funcionalidad relacionada.  
  
> [!NOTE]
>  Los elementos de atributo, cuyos nombres concluyen con la cadena Attribute, se pueden utilizar con la cadena o sin ella.  Por ejemplo, los dos ejemplos de código siguientes tienen un funcionamiento idéntico:  
>   
>  `[TestClass()]`  
>   
>  `[TestClassAttribute()]`  
  
### Elementos utilizados para preparar pruebas controladas por datos  
 Utilice los elementos siguientes para preparar pruebas unitarias controladas por datos.  Para obtener más información, vea [Cómo: Crear una prueba unitaria controlada por datos](../test/how-to-create-a-data-driven-unit-test.md) y [Tutorial: Utilizar un archivo de configuración para definir un origen de datos](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md).  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataAccessMethod>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataSourceAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataSourceElement>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataSourceElementCollection>  
  
## Atributos utilizados para establecer un orden de llamada  
 Un elemento de código decorado con uno de los atributos siguientes recibe una llamada en el momento en que se especifica.  Para obtener más información, vea [Anatomía de las pruebas unitarias](http://msdn.microsoft.com/es-es/a03d1ee7-9999-4e7c-85df-7d9073976144).  
  
### Para los ensamblados  
 Se llama a AssemblyInitialize y AssemblyCleanup inmediatamente después de que se cargue el ensamblado e inmediatamente antes de que se descargue.  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssemblyInitializeAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssemblyCleanupAttribute>  
  
### Para las clases  
 Se llama a ClassInitialize y ClassCleanup inmediatamente después de que se cargue la clase e inmediatamente antes de que se descargue.  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.ClassInitializeAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.ClassCleanupAttribute>  
  
### Para los métodos Test  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestInitializeAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestCleanupAttribute>  
  
## Atributos utilizados para identificar clases y métodos Test  
 Todas las clases Test deben tener el atributo TestClass y todos los métodos Test deben tener el atributo TestMethod.  Para obtener más información, vea [Anatomía de las pruebas unitarias](http://msdn.microsoft.com/es-es/a03d1ee7-9999-4e7c-85df-7d9073976144).  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestClassAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestMethodAttribute>  
  
## Clases Assert y excepciones relacionadas  
 Las pruebas unitarias pueden comprobar el comportamiento de aplicaciones concretas según su uso de diversos tipos de instrucciones, excepciones y atributos Assert.  Para obtener más información, vea [Utilizar las clases Assert](../test/using-the-assert-classes.md).  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.Assert>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.CollectionAssert>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.StringAssert>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssertFailedException>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssertInconclusiveException>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.UnitTestAssertException>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.ExpectedExceptionAttribute>  
  
## La clase TestContext  
 Los atributos siguientes y los valores que tienen asignados aparecen en la ventana Propiedades de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para un método Test determinado.  Estos atributos no están diseñados para que se permita el acceso a ellos mediante el código de la prueba unitaria.  Pero sí afectan a la manera en que se utiliza o se ejecuta la prueba unitaria, bien lo haga usted a través del IDE de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], o por el motor de pruebas de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Por ejemplo, algunos de estos atributos aparecen como columnas en la ventana Administrador de pruebas y en la ventana Resultados de pruebas, lo que significa que puede utilizarlos para agrupar y ordenar las pruebas y sus resultados.  Uno de estos atributos es TestPropertyAttribute, que se utiliza para agregar metadatos arbitrarios a las pruebas unitarias.  Por ejemplo, podría utilizarlo para almacenar el nombre de una prueba superada que cubre esta prueba, marcando la prueba unitaria con `[TestProperty("TestPass", "Accessibility")]`.  O podría utilizarlo para almacenar un indicador de la naturaleza de la prueba: `[TestProperty("TestKind", "Localization")]`.  La propiedad creada utilizando este atributo, y el valor que se le asigna, se muestran en la ventana Propiedades de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bajo el encabezado **Específico de la prueba**.  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.OwnerAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DeploymentItemAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DescriptionAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.HostTypeAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.IgnoreAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.PriorityAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestPropertyAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.WorkItemAttribute>  
  
## Clases de configuración de pruebas  
  
-   <xref:Microsoft.TeamFoundation.TestManagement.Client.ObjectTypes>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestConfigurationSection>  
  
## Atributos utilizados para generar informes  
 Los atributos de esta sección relacionan el método de prueba que decoran con entidades de la jerarquía de un proyecto de equipo de [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)].  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.CssIterationAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.CssProjectStructureAttribute>  
  
## Clases utilizadas con descriptores de acceso privados  
 Como se explica en [Using Publicize to Create a Private Accessor](http://msdn.microsoft.com/es-es/2056c6a7-6672-42a7-8f53-fead33c56deb), se puede generar una prueba unitaria para un método privado.  Esta generación crea una clase de descriptor de acceso privado, que crea instancias de un objeto de la clase PrivateObject.  La clase PrivateObject es una clase contenedora que utiliza la reflexión como parte del proceso del descriptor de acceso privado.  La clase PrivateType es similar, pero se utiliza para llamar a métodos estáticos privados, en lugar de a métodos de instancia privados.  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.PrivateObject>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.PrivateType>  
  
## Vea también  
 <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework>