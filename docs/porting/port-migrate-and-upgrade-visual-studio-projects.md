---
title: Portar, migrar y actualizar proyectos de Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 2/27/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Win8ExpressDesktopBlock
- w8trefactor
- VS.ReviewProjectAndSolutionChangesDialog.UpgradeRetarget
- ProjectCompatibilityDlgHelpTopic
- VS.ReviewProjectAndSolutionChangesDialog.Upgrade
helpviewer_keywords:
- conversion, projects
- asset compatibility
- projects, conversion
ms.assetid: bee759bd-6ff5-4c2e-913a-ea7d3c906c29
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: dac3cb1d7767c2ff76ac25f6a486ad30a8d54831
ms.openlocfilehash: 6b61cbc8460266ac305b12bf14f92d7445bfc900
ms.lasthandoff: 03/03/2017

---
# <a name="port-migrate-and-upgrade-visual-studio-projects"></a>Portar, migrar y actualizar proyectos de Visual Studio

Cada nueva versión de Visual Studio suele ser compatible con la mayoría de los tipos anteriores de proyectos, archivos y otros activos. Puede trabajar con ellos igual que ha hecho hasta ahora, y siempre y cuando no dependa de las características más recientes, Visual Studio mantendrá la compatibilidad con versiones anteriores, como Visual Studio 2015, Visual Studio 2013 y Visual Studio 2012. (Vea en [Notas de la versión](https://www.visualstudio.com/vs/release-notes/) las funciones específicas de cada versión).

A pesar de todo, la compatibilidad con algunos tipos puede cambiar a lo largo del tiempo. Una versión más reciente de Visual Studio podría no admitir ciertos tipos o requerir que se migren y se actualicen, de forma que ya no serán compatibles con versiones anteriores. En este tema se proporcionan detalles sobre los tipos de proyectos afectados en Visual Studio 2017. Encontrará una lista de los tipos admitidos en Visual Studio 2017 en el tema [Compatibilidad y destinatarios de la plataforma](https://www.visualstudio.com/productinfo/vs2017-compatibility-vs).

> [!Note]
> Para abrir determinados tipos de proyectos, será necesario agregar la carga de trabajo adecuada mediante el instalador de Visual Studio.


## <a name="projects"></a>Proyectos

En la lista siguiente se describe la compatibilidad de Visual Studio 2017 con proyectos creados en versiones anteriores. Si no ve un tipo de archivo o proyecto que debería estar incluido aquí, vea la [versión de Visual Studio 2015 de este tema](https://msdn.microsoft.com/library/hh266747.aspx) y notifíquelo más abajo en los comentarios.

| Tipo de proyecto | Compatibilidad |
| --- | --- |
| Proyectos de .NET Core (.xproj) | Los proyectos creados con Visual Studio 2015 usaban las herramientas de vista previa, que incluye un archivo de proyecto.xproj. Cuando abra un archivo .xproj con Visual Studio 2017, se le pedirá que migre el archivo al formato .csproj (se realiza una copia de seguridad del archivo .xproj). Este formato .csproj para los proyectos de .NET Core no se admite en VS2015 y versiones anteriores.  El formato .xproj no se admite en Visual Studio 2017, a menos que sea para la migración a .csproj. |
| Aplicación web ASP.NET y aplicación web ASP.NET Core con Application Insights habilitado | Para cada usuario de Visual Studio, la información de los recursos se almacena en el Registro por instancia de usuario. Se usa cuando el usuario no tiene abierto un proyecto y quiere buscar datos de Azure Application Insights. Visual Studio 2015 usa una ubicación del Registro diferente de la de Visual Studio 2017 y no entra en conflicto.<br/><br/>Una vez que un usuario crea una aplicación web ASP.NET o una aplicación web ASP.NET Core, el recurso se almacena en el archivo .suo. El usuario puede abrir el proyecto en Visual Studio 2015 o 2017 y la información de los recursos se usará para ambos, siempre y cuando Visual Studio sea compatible con los proyectos y las soluciones que se usan en las dos versiones. Los usuarios deberán autenticarse una vez en cada producto. Por ejemplo, si un proyecto se ha creado con Visual Studio 2015 y se abre en Visual Studio 2017, el usuario deberá autenticarse en Visual Studio 2017. |
| Webform o Windows Forms de C#/Visual Basic | Puede abrir el proyecto en Visual Studio 2017 y Visual Studio 2015. |
| Proyectos de prueba unitaria de base de datos (.csproj, .vbproj)    | Los proyectos de prueba unitaria de datos más antiguos se cargarán en Visual Studio 2017, pero usarán la versión con GAC de las dependencias. Para actualizar el proyecto de prueba unitaria de modo que use las dependencias más recientes, haga clic con el botón derecho en el proyecto en el Explorador de soluciones y seleccione **Convertir en proyecto de prueba unitaria de SQL Server…**. |
| F# | Visual Studio 2017 puede abrir proyectos creados en Visual Studio 2013 y 2015. Para habilitar las características de Visual Studio 2017 en estos proyectos, abra las propiedades del proyecto y cambie el destino fsharp.core a F# 4.1. |
| LightSwitch | LightSwitch ya no se admite en Visual Studio 2017. Los proyectos creados con Visual Studio 2012 y versiones anteriores que se abran en Visual Studio 2013 o Visual Studio 2015 se actualizarán y solo se podrán abrir en Visual Studio 2013 o Visual Studio 2015 a partir de entonces. |
| Microsoft Azure Tools para Visual Studio | Para abrir estos tipos de proyecto, instale primero el [SDK de Azure para .NET](http://azure.microsoft.com/en-us/downloads/)y luego abra el proyecto. Si es necesario, el proyecto se actualizará. |
| Marco de trabajo Model-View-Controller (ASP.NET MVC) | Compatibilidad con versiones de MVC y Visual Studio:<ul><li>Visual Studio 2010 SP1 admite MVC 2 y MVC 3. Se ha agregado compatibilidad con MVC 4 mediante la [descarga de ASP.NET 4 MVC 4 para Visual Studio 2010 SP1](https://www.microsoft.com/en-us/download/details.aspx?id=30683).</li><li>Visual Studio 2012 solo admite MVC 3 y MVC 4.</li><li>Visual Studio 2013 solo admite MVC 4 y MVC 5.</li><li>Visual Studio 2017 y Visual Studio 2015 admiten MVC 4 (puede abrir proyectos existentes, pero no crearlos) y MVC 5.</li></ul><br/><br/>Actualización de versiones de MVC:<ul><li>Para obtener información sobre cómo actualizar automáticamente MVC 2 a MCV 3, vea [Actualizador de aplicaciones ASP.NET MVC 3](http://go.microsoft.com/fwlink/?LinkID=238178).</li><li>Para obtener información acerca de cómo actualizar manualmente MVC 2 a MVC 3, vea [Herramientas para actualizar un proyecto ASP.NET MVC 2 a ASP.NET MVC 3](http://go.microsoft.com/fwlink/?linkid=238178).</li><li>Para obtener información acerca de cómo actualizar manualmente MVC 3 a MVC 4, vea [Actualizar un proyecto ASP.NET MVC 3 a ASP.NET MVC 4](http://www.asp.net/whitepapers/mvc4-release-notes). Si el proyecto tiene como destino .NET Framework 3.5 SP1, debe redestinarlo para que use .NET Framework 4.</li><li>Para obtener información sobre cómo actualizar manualmente MVC 4 a MVC 5, vea [How to Upgrade an ASP.NET MVC 4 and Web API Project to ASP.NET MVC 5 and Web API 2](https://www.asp.net/mvc/overview/releases/how-to-upgrade-an-aspnet-mvc-4-and-web-api-project-to-aspnet-mvc-5-and-web-api-2) (Cómo actualizar un proyecto ASP.NET MVC 4 y Web API a ASP.NET MVC 5 y Web API 2).</li></ul> |
| Modelado | Si permite que Visual Studio actualice el proyecto automáticamente, puede abrirlo en Visual Studio 2015, Visual Studio 2013 o Visual Studio 2012.<br/><br/>El formato del proyecto de modelado no ha cambiado entre Visual Studio 2015 y Visual Studio 2017, y el proyecto se puede abrir y modificar en cualquier versión. A pesar de todo, existen diferencias en el comportamiento de Visual Studio 2017:<ul><li>Los proyectos de modelado ahora se denominan proyectos de "Validación de dependencias" en los menús y las plantillas.</li><li>Los diagramas UML ya no se admiten en Visual Studio 2017. Los archivos UML se muestran en el Explorador de soluciones igual que antes, pero se abrirán como archivos XML. Use Visual Studio 2015 para ver, crear o editar los diagramas UML.</li><li>En Visual Studio 2017, la validación de dependencias arquitectónicas ya no se lleva a cabo cuando se compila el proyecto de modelado, sino que se realiza a medida que se compila cada proyecto de código. Este cambio no afecta al proyecto de modelado, pero requiere una serie de cambios en los proyectos de código que se están validando. Visual Studio 2017 puede realizar automáticamente los cambios necesarios en los proyectos de código ([más información](http://go.microsoft.com/fwlink/?LinkId=827800)).</li></ul> |
| Silverlight | Los proyectos de Silverlight no se admiten en Visual Studio 2017. Para conservar las aplicaciones de Silverlight, siga usando Visual Studio 2015. |
| Visual C++ | Puede usar Visual Studio 2017 para abrir soluciones y proyectos creados en Visual Studio 2015 tal como están, pero los proyectos creados en versiones anteriores de Visual Studio pueden requerir la actualización del proyecto o la redestinación a un conjunto de herramientas más reciente para compilar con Visual Studio 2017. Para obtener más información, vea [Cómo: Actualizar proyectos de Visual C++ a Visual Studio 2015](https://msdn.microsoft.com/en-us/library/hh690665.aspx) y [Guía de migración y actualización de Visual C++](https://msdn.microsoft.com/en-us/library/dn986839.aspx). |
| Extensibilidad de Visual Studio/VSIX | Los proyectos con MinimumVersion 14.0 o menos se actualizarán para que declaren MinimumVersion 15.0, lo que impide que el proyecto se abra en versiones anteriores de Visual Studio. Para permitir que un proyecto se abra en versiones anteriores, establezca MinimumVersion en `$(VisualStudioVersion)`. Vea también [How to: Migrate Extensibility Projects to Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md) (Cómo: Migrar proyectos de extensibilidad a Visual Studio 2017). |
| Visual Studio Lab Management | Puede usar Microsoft Test Manager o Visual Studio 2010 SP1 y versiones posteriores para abrir entornos creados en cualquiera de estas versiones. En el caso de Visual Studio 2010 SP1, la versión de Microsoft Test Manager debe coincidir con la versión de Team Foundation Server para poder crear entornos. |
| Visual Studio Tools para Apache Cordova |Este proyecto se puede abrir en Visual Studio 2017, pero no es compatible con versiones anteriores. Al abrir un proyecto de Visual Studio 2015, se le pedirá que permita realizar modificaciones en el proyecto. De este modo, se actualiza el proyecto para que use conjuntos de herramientas en lugar de un archivo `taco.json` para administrar el control de versiones de la biblioteca de Cordova, sus plataformas y complementos, y sus dependencias de nodo/npm. Vea la [guía de migración](http://taco.visualstudio.com/docs/vs-taco-2017-migration/) para obtener más información. |
| Windows Communication Foundation y Windows Workflow Foundation | Puede abrir este proyecto en Visual Studio 2017, Visual Studio 2015, Visual Studio 2013 y Visual Studio 2012. |
| Windows Presentation Foundation | Puede abrir este proyecto en Visual Studio 2013, Visual Studio 2012 y Visual Studio 2010 SP1. |
| Aplicaciones de la Tienda Windows/Windows Phone | Los proyectos para la Tienda Windows 8.1 y 8.0 y Windows Phone 8.1 y 8.0 no son compatibles con Visual Studio 2017. Para conservar estas aplicaciones, siga usando Visual Studio 2015. Para conservar los proyectos de Windows Phone 7.x, use Visual Studio 2012. |
