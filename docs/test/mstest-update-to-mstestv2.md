---
title: Actualización a MSTestV2
description: Obtenga información sobre cómo realizar la actualización de MSTestV1 a MSTestV2
ms.custom: SEO-VS-2020
ms.date: 02/26/2021
ms.topic: conceptual
f1_keywords:
- vs.UnitTest.Migrate
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ffe45c444321a7efbaee0a2eb5729850a06c5910
ms.sourcegitcommit: 99b66b0f4ced46ead0b2506a103f974f40cc0076
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/12/2021
ms.locfileid: "103366274"
---
# <a name="upgrade-from-mstestv1-to-mstestv2"></a>Actualización de MSTestV1 a MSTestV2

Puede actualizar el proyecto de prueba cambiando el destino de la versión de MSTest a la que se hace referencia en el archivo *.csproj* de MSTestV1 a MSTestV2. No se han incluido todas las características de MSTestV1 en MSTestV2, por lo que puede que sea necesario realizar algunos cambios para resolver los errores. Consulte [Características de MSTestV1 que no se admiten en MSTestV2](#mstestv1-features-that-are-not-supported-in-mstestv2) para entender qué características dejarán de funcionar. Puede que se tengan que quitar algunas de ellas de sus pruebas.

1. Quite la referencia de ensamblado a Microsoft.VisualStudio.QualityTools.UnitTestFramework del proyecto de prueba unitaria.
2. Añada referencias de paquetes NuGet a MSTestV2, incluidos los paquetes [MSTest.TestFramework](https://www.nuget.org/packages/MSTest.TestFramework) y [MSTest.TestAdapter](https://www.nuget.org/packages/MSTest.TestAdapter/) de nuget.org. Puede instalar paquetes en la consola del administrador de paquetes de NuGet con los siguientes comandos:

    ```console
    PM> Install-Package MSTest.TestAdapter -Version 2.1.2
    PM> Install-Package MSTest.TestFramework -Version 2.1.2
    ```

### <a name="old-style-csproj-example"></a>Ejemplo de .csproj de estilo antiguo

*.csproj* de muestra que tiene como destino MSTestV1:

```xml
<Reference Include="Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=10.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
  <Private>False</Private>
</Reference>
```

*.csproj* de muestra que ahora tiene como destino MSTestV2:

```xml
<Reference Include="Microsoft.VisualStudio.TestPlatform.TestFramework, Version=14.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
  <HintPath>..\packages\MSTest.TestFramework.2.1.2\lib\net45\Microsoft.VisualStudio.TestPlatform.TestFramework.dll</HintPath>
</Reference>
```

> [!NOTE]
> Los proyectos de prueba que son pruebas de IU codificadas o pruebas de carga web no son compatibles con MSTestV2. Estos tipos de proyectos han quedado en desuso. Obtenga más información en [Desuso de la prueba de IU codificada](https://devblogs.microsoft.com/devops/changes-to-coded-ui-test-in-visual-studio-2019/) y [Desuso de la prueba de carga web](https://devblogs.microsoft.com/devops/cloud-based-load-testing-service-eol/).

### <a name="sdk-style-csproj-net-core-and-net-5"></a>Archivo .csproj de estilo SDK (.NET Core y .NET 5)

Si su *.csproj* es el *.csproj* de estilo SDK más reciente, probablemente ya esté usando MSTestV2. Puede encontrar los paquetes NuGet para [MSTestV2](https://www.nuget.org/packages/MSTest.TestFramework) y el [adaptador de MSTestV2](https://www.nuget.org/packages/MSTest.TestAdapter/) en NuGet.

Ejemplo:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="16.7.1" />
  <PackageReference Include="MSTest.TestAdapter" Version="2.1.1" />
  <PackageReference Include="MSTest.TestFramework" Version="2.1.1" />
</ItemGroup>
```

## <a name="why-upgrade-to-mstestv2"></a>¿Por qué realizar la actualización a MSTestV2?

En 2016, publicamos el siguiente paso para desarrollar el marco de MSTest con MSTestV2. Puede leer más sobre este cambio en la [entrada de blog](https://devblogs.microsoft.com/devops/taking-the-mstest-framework-forward-with-mstest-v2/) del anuncio.

* MSTestV2 se adquiere y actualiza más fácilmente porque se entrega como un [paquete NuGet](https://www.nuget.org/packages/MSTest.TestFramework/).
* MSTestV2 es de [código abierto](https://github.com/microsoft/testfx).
* Compatibilidad con la plataforma de aplicaciones uniforme: MSTestV2 es una implementación que ofrece compatibilidad con la plataforma de aplicaciones uniforme en .NET Framework, .NET Core, ASP.NET Core y UWP. [Más información](https://blogs.msdn.microsoft.com/devops/2016/09/01/announcing-mstest-v2-framework-support-for-net-core-1-0-rtm/).
* La implementación es totalmente multiplataforma (Windows, Linux y Mac). [Más información](https://blogs.msdn.microsoft.com/devops/2017/04/05/mstest-v2-is-open-source/).
* MSTestV2 admite el uso como destino de .NET Framework 4.5.0 y versiones posteriores, .NET Core 1.0 y versiones posteriores (aplicaciones universales de Windows 10 y posteriores), ASP.NET Core 1.0 y versiones posteriores, y .NET 5 y versiones posteriores.
* Proporciona un mecanismo de extensibilidad de usuario final uniforme y único. [Más información](https://blogs.msdn.microsoft.com/devops/2017/07/18/extending-mstest-v2/).
* Proporciona una compatibilidad uniforme con `DataRow` para todos los proyectos de prueba basados en MSTest. [Más información](https://blogs.msdn.microsoft.com/devops/2017/02/25/mstest-v2-now-and-ahead/).
* Permite colocar el atributo `TestCategory` en el nivel de una clase o un ensamblado. [Más información](https://blogs.msdn.microsoft.com/devops/2017/02/25/mstest-v2-now-and-ahead/).
* Los métodos de prueba de las clases base definidas en otro ensamblado ahora se detectan y ejecutan desde la clase de prueba derivada. Este cambio aporta un comportamiento coherente con los tipos de clase de prueba derivados. Si este comportamiento no es necesario por motivos de compatibilidad, se puede volver a cambiar con los siguientes parámetros de ejecución:

    ```xml
    <RunSettings>    
    <MSTest> 
      <EnableBaseClassTestMethodsFromOtherAssemblies>false</EnableBaseClassTestMethodsFromOtherAssemblies> 
    </MSTest> 
    </RunSettings>
    ```

* Proporciona un control más preciso sobre la ejecución en paralelo mediante la [ejecución en paralelo en ensamblado](https://github.com/Microsoft/testfx-docs/blob/master/RFCs/004-In-Assembly-Parallel-Execution.md) de pruebas. Esto permite ejecutar pruebas dentro de un ensamblado en paralelo.
* El método `TestCleanup` en `TestClass` se invoca incluso aunque se produzca un error en su método `TestInitialize` correspondiente. [Detalles del problema](https://github.com/Microsoft/testfx/issues/250).
* El tiempo que tardan `AssemblyInitialize` y `ClassInitialize` no se cuenta para la duración de la prueba. Este cambio limita su impacto en el tiempo de espera de la prueba.
* Las pruebas que no son ejecutables se pueden configurar para que se marquen como erróneas mediante la etiqueta `MapNotRunnableToFailed`, que forma parte del nodo de adaptador en el archivo `.runsettings`.

    ```xml
    <RunSettings>    
    <MSTest> 
      <MapNotRunnableToFailed>true</MapNotRunnableToFailed> 
    </MSTest> 
    </RunSettings>
    ```

## <a name="mstestv1-features-that-are-not-supported-in-mstestv2"></a>Características de MSTestV1 que no se admiten en MSTestV2

*   Las pruebas no se pueden incluir en una "prueba por orden".
*   El adaptador no admite la configuración mediante un archivo *.testsettings*. Use el nuevo [archivo *.runsettings*](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md) para la configuración de la serie de pruebas.
*   El adaptador no admite listas de pruebas especificadas como un archivo *.vsmdi*.
*   No se admiten los tipos "Proyecto de prueba de IU codificada" ni "Proyecto de prueba de carga y rendimiento web". Obtenga más información en [Desuso de la prueba de IU codificada](https://devblogs.microsoft.com/devops/changes-to-coded-ui-test-in-visual-studio-2019/) y [Desuso de la prueba de carga web](https://devblogs.microsoft.com/devops/cloud-based-load-testing-service-eol/).

## <a name="see-also"></a>Consulte también

- [Configuración de serie de pruebas con `.runsettings`](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
- [Haga una prueba unitaria de su código](../test/unit-test-your-code.md)
- [Depurar pruebas unitarias con el Explorador de pruebas](../test/debug-unit-tests-with-test-explorer.md)
