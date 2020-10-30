---
title: Inventario de preproducción en la suscripción de Visual Studio | Visual Studio Marketplace
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 7d74e113-8fb2-490e-8502-48cce7b1327a
ms.date: 10/22/2020
ms.topic: conceptual
description: Obtenga información sobre la responsabilidad de los administradores de realizar inventarios de preproducción
ms.openlocfilehash: b464a7d9cfa8c802cd2367c5c7d0e76141583f3a
ms.sourcegitcommit: bf5e2bba5acdcf05869b861211f8bb755081e5ce
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2020
ms.locfileid: "92467432"
---
# <a name="inventory-of-pre-production-environment"></a>Inventario de entorno de preproducción
Las suscripciones de Visual Studio simplifican la administración de activos realizando un recuento de los usuarios en lugar de los dispositivos.

Los administradores de Visual Studio deben asignar Suscripciones de Visual Studio a **usuarios con nombre específicos** . **No se permiten** las convenciones de nomenclatura como Dev1 o Dev2 ni el uso de nombres de equipo como "FeatureTeam".

Estas son algunas maneras de simplificar el inventariado del entorno de preproducción:
- Revise las asignaciones de usuario. Microsoft proporciona un sitio web denominado [Portal de administración de Visual Studio](https://manage.visualstudio.com/) que le permite realizar un seguimiento de las asignaciones de suscripciones de Visual Studio.
- Use su versión de Active Directory local o basada en la nube para enumerar usuarios. Si usa Active Directory para administrar el acceso de usuarios, es posible que pueda identificar los usuarios de desarrollo y pruebas por su pertenencia al directorio.
- Use herramientas automatizadas para crear inventarios de sistemas. Es posible que también tenga que usar una herramienta de inventario de software para ayudarle a administrar sus activos de software y distinguir los entornos de preproducción de los entornos de producción. Muchos clientes con Microsoft System Center crean convenciones de nomenclatura para ayudar a automatizar esta parte del proceso de inventariado.
- Obtenga ayuda con la conciliación manual. Apunte al personal para que le ayude a conciliar los usuarios de desarrollo y pruebas con el entorno de desarrollo y pruebas.

## <a name="resources"></a>Recursos
- [Notas sobre la concesión de licencias de Visual Studio](https://visualstudio.microsoft.com/wp-content/uploads/2019/06/Visual-Studio-Licensing-Whitepaper-May-2019.pdf)
- [Soporte técnico para suscripciones y administración de Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs)
- [Términos de las licencias por volumen](https://www.microsoft.com/licensing/product-licensing/products.aspx)

## <a name="see-also"></a>Consulte también
- [Documentación de Visual Studio](/visualstudio/)
- [Documentación de Azure DevOps](/azure/devops/)
- [Documentación de Azure](/azure/)
- [Documentación de Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Pasos siguientes
Obtenga más información sobre las responsabilidades de los administradores:
- [Responsabilidades del administrador](admin-responsibilities.md)
- [Administración de equipos grandes y contratistas externos](manage-teams.md)
- [Seguimiento de las asignaciones de usuarios y tramitación de pedidos](assignments-orders.md)
- Emplee [Uso máximo](maximum-usage.md) para realizar el seguimiento de los compromisos de compra