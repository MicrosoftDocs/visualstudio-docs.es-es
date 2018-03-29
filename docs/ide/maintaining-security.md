---
title: Mantenimiento de la seguridad de la aplicación en Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: article
helpviewer_keywords:
- unauthorized access
- Baseline Security Analyzer
- Microsoft Baseline Security Analyzer
- security [.NET Framework], best practices
- MBSA (Microsoft Baseline Security Analyzer)
- security [.NET Framework], maintaining after deployment
ms.assetid: 621d10c1-842b-4902-be60-bb9719591751
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: f0594f7c9af507f2c68ac4f0cc80b1d2e38d2a51
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/15/2018
---
# <a name="maintaining-security"></a>Mantener la seguridad

Suele decirse que para obtener seguridad no hay que bajar la guardia. A pesar de todo el esfuerzo que pueda dedicar al sistema de seguridad durante las fases de diseño y desarrollo de la aplicación, debe asumir que después de la implementación surgirán errores en el sistema de seguridad. La auditoría de la aplicación y el análisis de los registros de eventos permiten detectar algunos errores que antes estaban ocultos.

Además, no sólo debe supervisar su propia aplicación sino que también debe mantenerse al día en relación con nuevas amenazas y errores en el sistema de seguridad de la plataforma en la que se ejecuta la aplicación y de otros productos de los que dependa la aplicación.

[Seguridad, privacidad y cuentas](https://support.microsoft.com/products/microsoft-account?category=privacy#security-privacy-accounts-help=windows-8&v0h=winrttab1&v1h=win8tab1&v2h=win7tab1&v3h=winvistatab1)&mdash;Obtenga ayuda con la seguridad, la privacidad y las cuentas de usuario, con información sobre virus, contraseñas, controles parentales, firewalls y cifrado de unidades.

[Boletín de seguridad de Microsoft](https://technet.microsoft.com/security/bulletins.aspx)&mdash;Esta página facilita la búsqueda de boletines anteriores. Dirigidos a los profesionales informáticos (IT), los boletines de seguridad proporcionan información detallada relativa a las actualizaciones de seguridad.

[Microsoft Baseline Security Analyzer ](https://www.microsoft.com/download/details.aspx?id=7558)&mdash;Microsoft Baseline Security Analyzer (MBSA) es una herramienta que permite a un usuario individual, a un usuario corporativo o a un administrador buscar en uno o más equipos con Windows errores comunes en la configuración de seguridad.