---
title: Página de propiedades Aplicación para aplicaciones UWP
description: Aprenda a usar la página Aplicación para especificar la información del paquete y el ensamblado del proyecto de la Plataforma universal de Windows (UWP), y definir como destino la versión de Windows 10.
ms.custom: SEO-VS-2020
ms.date: 01/23/2018
ms.topic: reference
f1_keywords:
- AppPackage.Properties.Application
helpviewer_keywords:
- Application page [UWP project]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- uwp
ms.openlocfilehash: 21dd08f81802661cae9d77ee3449f4e9369ca768
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965088"
---
# <a name="application-property-page-uwp-projects"></a>Página de propiedades de Aplicación (proyectos UWP)

Use la página de propiedades de **Aplicación** para especificar la información de paquete y ensamblado del proyecto de Plataforma universal de Windows (UWP), así como para especificar la versión de Windows 10 como destino.

![Página de propiedades de aplicación](media/application-page-uwp.png)

Para acceder a la página **Aplicación**, seleccione el nodo de proyecto en el **Explorador de soluciones**. Después, seleccione **Proyecto** > **Propiedades** en la barra de menús. Las páginas de propiedades se abren en la pestaña **Aplicación**.

## <a name="general-section"></a>Sección general

**Nombre del ensamblado**&mdash;Especifica el nombre del archivo de salida que contendrá el manifiesto del ensamblado.

Para obtener acceso a esta propiedad mediante programación, vea <xref:VSLangProj.ProjectProperties.AssemblyName%2A>.

**Espacio de nombres predeterminado**&mdash;Especifica el espacio de nombres base para los archivos agregados al proyecto. Para obtener más información acerca de los espacios de nombres, vea [Espacios de nombres (Guía de programación de C#)](/dotnet/csharp/programming-guide/namespaces/), [Espacios de nombres en Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/namespaces) o [Espacios de nombres (C++)](/cpp/cpp/namespaces-cpp).

Para obtener acceso a esta propiedad mediante programación, vea <xref:VSLangProj.ProjectProperties.RootNamespace%2A>.

**Información de ensamblado**&mdash;Al hacer clic en este botón se muestra el [cuadro de diálogo Información de ensamblado](../../ide/reference/assembly-information-dialog-box.md).

**Manifiesto del paquete**&mdash;Al elegir este botón se abre el diseñador de manifiestos. También es posible acceder al diseñador de manifiestos por medio del archivo _Package.appxmanifest_ en el **Explorador de soluciones**. Para obtener más información, consulte [Configurar un paquete con el diseñador de manifiestos](/windows/msix/package/packaging-uwp-apps#configure-your-project)

## <a name="targeting-section"></a>Sección de selección de destino

Puede establecer la versión de destino y la versión mínima de Windows 10 para la aplicación mediante las listas desplegables de esta sección. Se recomienda que se dirija a la versión más reciente de Windows 10, y si está desarrollando una aplicación empresarial, que admita también una versión anterior mínima. Para obtener más información acerca de qué versión de Windows 10 elegir, consulte [Elegir una versión de UWP](/windows/uwp/updates-and-versions/choose-a-uwp-version).

Para obtener información sobre la selección de destinos de plataforma en Visual Studio, vea [Compatibilidad y destinatarios de la plataforma](/visualstudio/productinfo/vs2017-compatibility-vs#platform-targeting).

## <a name="see-also"></a>Consulte también

- [Crear su primera aplicación](/windows/uwp/get-started/your-first-app)
- [Elegir una versión de UWP](/windows/uwp/updates-and-versions/choose-a-uwp-version)
