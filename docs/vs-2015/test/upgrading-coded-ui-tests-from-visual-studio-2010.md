---
title: Actualizar pruebas de IU codificadas
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 11232a83-73ea-46bd-bc0c-46f74f6e3a42
caps.latest.revision: 35
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 54ccd9ad0cfefe33be7c51d44e9adb6c15717a7a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54803632"
---
# <a name="upgrading-coded-ui-tests-from-visual-studio-2010"></a>Actualizar pruebas de IU codificadas desde Visual Studio 2010
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los proyectos de prueba que contienen pruebas de IU codificadas creadas en [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] SP1 se reparan automáticamente al abrirse en Visual Studio 2012. Si los proyectos de prueba están protegidos bajo control de código fuente, los archivos del proyecto se desprotegen para esta reparación. Una vez reparados, estos proyectos de prueba que contienen pruebas de IU codificadas se pueden usar en [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] SP1 y [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].

 **Requisitos**

-   Visual Studio Enterprise

> [!NOTE]
>  Visual Studio incluye más de un tipo de proyecto de prueba. Si crea una nueva prueba de IU codificada, se creará en un tipo de proyecto de prueba de IU codificada. Para obtener más información, vea [Actualizar pruebas de versiones anteriores de Visual Studio](http://msdn.microsoft.com/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52).

> [!WARNING]
>  Los proyectos de prueba de[!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] que contienen pruebas de IU codificadas tienen que volver a compilarse al abrir el proyecto de prueba en [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] o [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] en paralelo con [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].

> [!WARNING]
>  Si un proyecto de prueba creado en [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] que solo contiene pruebas unitarias se abre en [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], no es posible agregarle las pruebas de IU codificadas. De forma similar, no se puede agregar una prueba de IU codificada a un proyecto de prueba unitaria creado en [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].

## <a name="compatibility-issues-between-visual-studio-2010-and-visual-studio-2012"></a>Problemas de compatibilidad entre Visual Studio 2010 y Visual Studio 2012
 En la siguiente tabla se enumeran los problemas que hay que tener en cuenta a la hora de migrar pruebas de IU codificadas entre [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] y [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].

> [!CAUTION]
>  Hay un problema conocido consistente en que las referencias de los proyectos de prueba de IU codificada no aparecen en el Explorador de soluciones. Para obtener más información, vea el archivo Léame incluido en el soporte de instalación de [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] .

|Funcionalidad de IU codificada|Problema|Soluciones|
|----------------------------|-----------|--------------|
|Las pruebas de IU de Silverlight no se admiten en [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].|**Se producirá un error de compilación**<br /><br /> Si tiene el Feature Pack 2 de [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] y ha creado proyectos de prueba de IU codificada para aplicaciones de Silverlight, estos proyectos no se pueden abrir en [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].|Se recomienda administrar estos proyectos únicamente en el Feature Pack 2 de [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] .|
|Las pruebas de IU de Firefox no se admiten en [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]|**La compilación será correcta, pero se producirá un error de ejecución de las pruebas**<br /><br /> Si tiene el Feature Pack 2 de [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] y ha creado proyectos de prueba de IU codificada para aplicaciones web de Firefox, estos proyectos no se pueden abrir en [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].|Se recomienda administrar estos proyectos únicamente en el Feature Pack 2 de [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] .|
|Se han agregado nuevas API de pruebas de código de IU en [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]|**Se producirá un error de compilación**<br /><br /> Si crea pruebas de IU codificadas mediante la nueva API de pruebas de IU en [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], no se podrán abrir estos proyectos en [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)].|Los proyectos que usen la nueva API únicamente deben administrarse en [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].|
|En [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] se agregaron referencias dentro de una instrucción ‘Choose’ en el archivo csproj. En [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] se está usando un archivo de destinos Feedback para incluir referencias de ensamblado de prueba de IU codificada.|En [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], una prueba de IU codificada no se puede agregar a un proyecto de prueba creado en [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] (o SP1) que no contuviera una prueba de IU codificada.<br /><br /> El proceso de reparación agrega el archivo de destinos y la instrucción Choose. Si una prueba de IU codificada no está en el proyecto de prueba, el proyecto se marca como reparado y no se agregarán las referencias adecuadas al agregar la prueba de IU codificada en [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].|Tendrá que crear un nuevo proyecto de prueba en la misma solución mediante [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] y agregarle la nueva prueba de IU codificada. Como alternativa, puede agregar pruebas de IU codificadas al proyecto de prueba en [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] SP1 y abrir dicho proyecto en [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].|

##  <a name="UpgradingCodedUIFromVS2010_Update"></a> Actualización de Visual Studio 2010 SP1
 Hay una actualización para [!INCLUDE[vs2010](../includes/vs2010-md.md)] SP1 con compatibilidad con Visual Studio 2012 y Windows 8 disponible para su descarga en el [Centro de descarga de Microsoft](http://www.microsoft.com/download/details.aspx?id=34677) y también como una actualización de Visual Studio.

 Después de aplicar la actualización, se mejoran las siguientes características de herramientas de prueba de IU codificada de [!INCLUDE[vs2010](../includes/vs2010-md.md)] SP1 para Windows 8:

- Puede ejecutar una prueba de IU codificada para los controles de Windows Presentation Foundation (WPF) basados en Microsoft .NET Framework 4.5 en un equipo que ejecute Windows 8.

- Puede ejecutar una prueba de IU codificada para Internet Explorer 10 de 64 bits (x64) en un equipo que ejecute Windows 8.

  La actualización también contiene correcciones para los siguientes problemas:

- **Cobertura de código:** incapacidad de abrir un archivo de cobertura de código (.coverage) creado por Visual Studio 2012 en [!INCLUDE[vs2010](../includes/vs2010-md.md)] SP1.

- **Artefactos de prueba inútiles:** el equipo tiene un artefacto de prueba asignado a un usuario no válido en Team Foundation Server (TFS) 2010. Por ejemplo, un usuario ha dejado la empresa, pero sigue teniendo un caso de prueba asignado. Actualice TFS 2010 a TFS 2012. Use [!INCLUDE[TCMext](../includes/tcmext-md.md)] 2010 para conectar con el servidor de TFS actualizado. No puede asignar el artefacto de prueba a ningún usuario de TFS con [!INCLUDE[TCMext](../includes/tcmext-md.md)] 2010.

- **Pruebas de carga:** al ejecutar una prueba de carga junto con un tipo de red distinto al perfil de red de área local (LAN) en un equipo que ejecuta Windows 8, el controlador de emulación de red hace que el sistema operativo se bloquee. Para más información, vea el [Artículo de KB 2736182](http://support.microsoft.com/kb/2736182).

## <a name="see-also"></a>Vea también
 [Portar, migrar y actualizar proyectos de Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md) [actualizar pruebas de versiones anteriores de Visual Studio](http://msdn.microsoft.com/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52) [usar UI Automation para probar el código](../test/use-ui-automation-to-test-your-code.md) [generar una Prueba de IU de grabación de acciones existente codificada](http://msdn.microsoft.com/library/56736963-9027-493b-b5c4-2d4e86d1d497) [configuraciones y plataformas compatibles para las pruebas de IU codificadas y las grabaciones de acciones](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
