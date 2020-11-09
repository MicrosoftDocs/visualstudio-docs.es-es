---
title: Implementación de ClickOnce en Windows Vista | Microsoft Docs
description: Obtenga información sobre cómo Visual Studio genera un manifiesto de UAC externo para ClickOnce y Registration-Free aplicaciones COM, que requieren un manifiesto externo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- UAC manifest generation
- ClickOnce deployment, Windows
- manifest generation
- Windows, ClickOnce deployment
ms.assetid: b21a0ebc-0ff6-4f49-8993-7d1ad3f8cac2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c2e09225339a87c55c31d27d26b129e199385e99
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2020
ms.locfileid: "94383084"
---
# <a name="clickonce-deployment-on-windows-vista"></a>Implementación de ClickOnce en Windows Vista

La compilación de aplicaciones en Visual Studio para el control de cuentas de usuario (UAC) en Windows Vista normalmente genera un manifiesto incrustado, codificado como datos XML binarios en el archivo ejecutable de la aplicación.  ClickOnce y Registration-Free aplicaciones COM requieren un manifiesto externo, por lo que Visual Studio genera un archivo para estos proyectos que contienen los datos de UAC en lugar de un manifiesto incrustado. En el caso de las implementaciones de ClickOnce y Registration-Free COM, Visual Studio usa información de un archivo denominado *app. manifest* para generar información externa del manifiesto de UAC. En todos los demás casos, Visual Studio incrusta los datos de UAC en el archivo ejecutable de la aplicación.

Visual Studio proporciona las siguientes opciones para la generación de manifiestos:

- Usar un manifiesto incrustado. Inserte los datos de UAC en el archivo ejecutable de la aplicación y ejecútelo como usuario normal.

   Esta es la configuración predeterminada (a menos que use ClickOnce). Esta configuración admite la manera habitual en la que Visual Studio funciona en Windows Vista, con la generación de un manifiesto interno y externo mediante `AsInvoker` .

- Use un manifiesto externo. Genere un manifiesto externo mediante *app. manifest*.

   Esto genera solo el manifiesto externo mediante la información de *app. manifest*. Al publicar una aplicación mediante ClickOnce o Registration-Free COM, Visual Studio agrega *app. manifest* al proyecto y, a continuación, agrega esta opción.

- No usar ningún manifiesto. Cree la aplicación sin un manifiesto.

   Este enfoque también se conoce como *Virtualización*. Use esta opción para la compatibilidad con las aplicaciones existentes de versiones anteriores de Visual Studio.

  Las nuevas propiedades están disponibles en la página **aplicación** del diseñador de proyectos (solo para proyectos de Visual C#) y en el formato de archivo de proyecto de MSBuild.

  El método para configurar la generación de manifiestos de UAC en el IDE de Visual Studio difiere según el tipo de proyecto (Visual C# o Visual Basic).

  * Para obtener información sobre la configuración de proyectos de Visual C# para la generación de manifiestos, vea [Página de aplicación, diseñador de proyectos (C#)](../ide/reference/application-page-project-designer-csharp.md).

  * Para obtener información sobre cómo configurar proyectos de Visual Basic para la generación de manifiestos, vea [Página de aplicación, diseñador de proyectos (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).

## <a name="see-also"></a>Vea también
- [Seguridad e implementación de ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Permisos de usuario y Visual Studio](/previous-versions/ms165100(v=vs.100))
- [Página de aplicación, Diseñador de proyectos (C#)](../ide/reference/application-page-project-designer-csharp.md)
- [Página de aplicación, Diseñador de proyectos (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)