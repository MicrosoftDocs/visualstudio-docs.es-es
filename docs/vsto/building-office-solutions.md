---
title: Compilar soluciones de Office
description: Obtenga información sobre las diferencias entre compilar y depurar proyectos de Office y compilar y depurar otros tipos de proyectos en Visual Studio, como Windows Forms.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- debugging [Office development in Visual Studio]
- debugging Office applications in Visual Studio
- solutions [Office development in Visual Studio], debugging
- Office applications [Office development in Visual Studio], debugging
- application development [Office development in Visual Studio], building
- Office applications [Office development in Visual Studio], building
- projects [Office development in Visual Studio], debugging
- Office solutions [Office development in Visual Studio], building
- solutions [Office development in Visual Studio], building
- Office projects [Office development in Visual Studio], debugging
- projects [Office development in Visual Studio], building
- builds [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], building
- application development [Office development in Visual Studio], debugging
- Office solutions [Office development in Visual Studio], debugging
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 31cb28ad2c332d0afea9bef8cbe1c979b58536e6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896710"
---
# <a name="build-office-solutions"></a>Compilar soluciones de Office
  En general, compilar y depurar proyectos de Office se hace de la misma manera que al compilar y depurar otros tipos de proyectos en Visual Studio, como Windows Forms. Los temas de esta sección explican las diferencias que existen entre ellos. Para obtener información general sobre cómo compilar aplicaciones, consulte [compilar y compilar en Visual Studio](../ide/compiling-and-building-in-visual-studio.md).

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="project-output-for-office-projects"></a>Resultados del proyecto para los proyectos de Office
 La ubicación de salida de los proyectos de Office es *nombreDeProyecto*\bin\release o *nombreDeProyecto*\bin\debug. Tenga en cuenta que la compilación no se puede realizar en los directorios de implementación.

### <a name="document-level-projects"></a>Proyectos de nivel de documento
 Cuando se compila un proyecto de nivel de documento, se incluyen los siguientes elementos en el resultado del proyecto:

- Una copia del documento del proyecto.

- El ensamblado de proyecto y todos los ensamblados a los que se hace referencia y que tienen la propiedad **Copia local** establecida en **true**.

- El manifiesto de aplicación, que tiene la extensión de nombre de archivo *. manifest*. Para obtener más información, consulte [manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md).

- El manifiesto de implementación, que tiene la extensión de nombre de archivo *. VSTO*. Para obtener más información, vea [manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md).

- Un archivo de base de datos de programa (*PDB*).

> [!NOTE]
> Si compila una solución de nivel de documento en una ubicación remota en lugar de en el equipo local, agregue la ruta de acceso completa a la lista Ubicaciones de confianza en el Centro de confianza de la aplicación. Para obtener más información, consulte la sección denominada otorgar confianza a los documentos en [soluciones seguras de Office](../vsto/securing-office-solutions.md).

### <a name="application-level-projects"></a>Proyectos de nivel de aplicación
 Al compilar un proyecto de complemento de VSTO, se incluyen los siguientes elementos en el resultado del proyecto:

- El ensamblado de proyecto y todos los ensamblados a los que se hace referencia y que tienen la propiedad **Copia local** establecida en **true**.

- El manifiesto de aplicación, que tiene la extensión de nombre de archivo *. manifest*. Para obtener más información, consulte [manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md).

- El manifiesto de implementación, que tiene la extensión de nombre de archivo *. VSTO*. Para obtener más información, vea [manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md).

- Un archivo de base de datos de programa (*PDB*) para el ensamblado del proyecto.

  El proceso de compilación de los proyectos de complemento VSTO también crea en el equipo de desarrollo un conjunto de entradas de registro que son necesarias para cargar el complemento VSTO. Para obtener más información, vea [entradas del registro para complementos de VSTO](../vsto/registry-entries-for-vsto-add-ins.md).

  Si compila un proyecto de complemento VSTO de Outlook que contiene áreas de formulario, el proceso de compilación agrega la siguiente información adicional al registro:

- Una clave para cada clase de mensaje asociada a una o varias áreas de formulario.

- Una entrada para cada área de formulario y un valor asociado que representa el nombre del complemento de VSTO de Outlook.

  Outlook necesita esta información para cargar las áreas de formulario.

## <a name="referenced-assemblies"></a>Ensamblados a los que se hace referencia
 Puede hacer referencia a los ensamblados (incluidos los proyectos de biblioteca de clases), desde el proyecto Compilar soluciones de Office. Todos los ensamblados a los que se hace referencia incluyen una propiedad llamada **Copia local**. La propiedad **Copia local** indica si el ensamblado se debe copiar en el directorio de resultados. De forma predeterminada, se establece en **true**. Todos los ensamblados a los que se haga referencia y que tengan la propiedad **Copia local** establecida en **true** se copiarán en el directorio de resultados.

## <a name="security-during-the-build-process"></a>Seguridad durante el proceso de compilación
 Visual Studio establece automáticamente la configuración de seguridad del equipo de desarrollo para hacer que la solución sea fiable durante el proceso de compilación. Esto permite ejecutar la solución mientras se depura.

 Los proyectos de Office usan certificados para comprobar los datos del publicador. Para ello, Visual Studio crea automáticamente un certificado temporal para identificar las soluciones de Office, y configura el equipo de desarrollo para conceder cierto grado de fiabilidad a este certificado temporal.

 Para obtener más información, vea [proteger soluciones de Office](../vsto/securing-office-solutions.md).

### <a name="network-projects"></a>Proyectos de red
 Si la ubicación del ensamblado o del documento se encuentra en un recurso compartido de red, la actualización de las directivas de seguridad local (a nivel de usuario) no es suficiente para permitir la ejecución de la solución. En cuanto a los ensamblados y a los documentos que se encuentren en un recurso compartido de red, es el administrador quien debe conceder plena confianza a nivel de equipo, para que se pueda ejecutar la solución. Para obtener más información acerca de cómo establecer la Directiva de seguridad, consulte [protección de soluciones de Office](../vsto/securing-office-solutions.md).

 En los proyectos de nivel de documento también debe agregar la ubicación completa del documento en la lista de carpetas de confianza de Office. Para obtener más información, vea [conceder confianza a los documentos](../vsto/granting-trust-to-documents.md).

## <a name="change-the-platform-target"></a>Cambiar el destino de la plataforma
 De forma predeterminada, el destino de la plataforma para los proyectos de Office es **Cualquier CPU**. No debería cambiar esta configuración si no es necesario. Las soluciones de Office que se compilan con la configuración de destino de la plataforma **Cualquier CPU** , se ejecutan en versiones de 32 bits y de 64 bits de Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] o [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)].

 Debe establecer el destino de la plataforma en x64 solamente si está creando una solución que se ejecutará en las versiones de 64 bits de Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] o de [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)], y si la solución llama a las API nativas de 64 bits. Para obtener más información sobre cómo cambiar la configuración de destino de la plataforma, consulte [Cómo: configurar proyectos para plataformas de destino](../ide/how-to-configure-projects-to-target-platforms.md).

 Si establece el destino de la plataforma en x64, la solución no se ejecutará en las versiones de 32 bits de Windows o de Office. El destino de plataforma x64 requiere que la solución se ejecute en un proceso de 64 bits.

## <a name="use-the-clean-command"></a>Usar el comando limpiar
 Para quitar los archivos de proyecto compilados del equipo de desarrollo, puede usar el comando **Limpiar** del menú **Compilar** en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. El comando **Limpiar** elimina todos los archivos de la ubicación de salida de la compilación. En los proyectos de nivel de aplicación, el comando **Limpiar** también quita las entradas de registro creadas por el proceso de compilación.

## <a name="related-topics"></a>Temas relacionados

|Title|Descripción|
|-----------|-----------------|
|[Depurar proyectos de Office](../vsto/debugging-office-projects.md)|Indica los problemas implicados en la depuración de proyectos de Office.|
|[Tutorial: crear la primera personalización de nivel de documento para Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)|Muestra cómo crear una personalización básica de nivel de documento para Excel.|
|[Cómo: volver a habilitar un complemento de VSTO que se ha deshabilitado](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)|Describe cómo volver a habilitar un complemento de VSTO que se ha deshabilitado de forma rígida o parcial.|
|[Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)|Proporciona vínculos a información sobre la creación de soluciones de Office y sobre el rol de los ensamblados en la solución.|