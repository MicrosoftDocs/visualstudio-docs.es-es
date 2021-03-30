---
title: Microsoft Windows Virtual Desktop en suscripciones de Visual Studio | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 872c5746-5357-4764-949b-aa525a0adf1a
ms.date: 03/17/2021
ms.topic: conceptual
description: Obtenga información sobre cómo puede aprovechar Microsoft Windows Virtual Desktop a través de la suscripción de Visual Studio
ms.openlocfilehash: 2e7aad5d3f8214d39e5671e4bf5c4d5d357cd930
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2021
ms.locfileid: "104671744"
---
# <a name="access-windows-virtual-desktop-in-subscriptions"></a>Acceso a Windows Virtual Desktop en las suscripciones 
Ahora los suscriptores de Visual Studio pueden usar sus créditos individuales de desarrollo y pruebas de Azure para los servicios de Microsoft Windows Virtual Desktop.  
Windows Virtual Desktop es un servicio completo de virtualización de escritorio y de aplicaciones que se ejecuta en la nube. Es la única Infraestructura de escritorio virtual (VDI) que ofrece administración simplificada, multisesión de Windows 10, optimizaciones para aplicaciones de Microsoft 365 para empresas y compatibilidad con entornos de Servicios de Escritorio remoto (RDS). Implemente y escale los escritorios y las aplicaciones Windows en Azure en cuestión de minutos y obtenga características integradas de cumplimiento y seguridad.
A continuación se indica lo que se puede hacer al ejecutar Windows Virtual Desktop en Azure:
- Configurar una implementación de Windows 10 de sesión múltiple que ofrezca toda la funcionalidad de Windows 10 con escalabilidad
- Virtualizar las aplicaciones de Microsoft 365 para la empresa y optimizarlo para ejecutarse en escenarios virtuales multiusuario
- Proporcionar escritorios virtuales de Windows 7 con actualizaciones gratuitas de seguridad ampliada
- Llevar sus aplicaciones y escritorios existentes de Servicios de Escritorio remoto (RDS) y Windows Server a cualquier equipo
- Virtualizar escritorios y aplicaciones
- Administre aplicaciones y escritorios de Windows 10, Windows Server y Windows 7 con una experiencia de administración unificada. Para obtener más información sobre lo que puede hacer con Windows Virtual Desktop, vea el [vídeo de introducción](/azure/virtual-desktop/overview).

## <a name="use-windows-virtual-desktop-with-azure"></a>Uso de Windows Virtual Desktop con Azure 
Ahora, los suscriptores de Visual Studio tienen varias formas de usar las suscripciones de Azure para pagar los servicios de Windows Virtual Desktop:
- [Créditos individuales de Azure DevTest](vs-azure.md).  Los suscriptores que reciben créditos individuales de Azure DevTest como parte de sus suscripciones pueden usarlos para pagar los servicios de Windows Virtual Desktop.  La cantidad del crédito mensual depende del nivel de suscripción.
- [Suscripciones de Pago por uso de Azure DevTest](vs-azure-payg.md).  Puede crear suscripciones de Azure y asociar un instrumento de pago para tener una manera sin problemas de pagar por el uso de Windows Virtual Desktop. 
- [Oferta de Contrato Enterprise de Azure DevTest](azure-ea-devtest.md).  Con esta oferta, los suscriptores con contratos Enterprise pueden pagar Windows Virtual Desktop con Azure a precios con descuento. 

## <a name="requirements"></a>Requisitos
Windows Virtual Desktop requiere una instancia de Azure Active Directory (Azure AD) a la que unir las máquinas virtuales.  Los usuarios deben ser miembros de esta instancia de Azure AD.  Hay dos opciones para implementar Azure AD:
- Servicios de Azure AD Directory.  Para la mayoría de los usuarios, esta es la opción más sencilla de implementar.
- Promoción de una máquina virtual en la que se ejecute un controlador de dominio.  Esta opción requiere más trabajo de configuración, pero ofrece a la mayoría de los usuarios un menor costo operativo.
Para ver una lista completa de los requisitos previos para usar Windows Virtual Desktop, visite la [página de información general](/azure/virtual-desktop/overview#requirements) de Windows Virtual Desktop. 

## <a name="get-started"></a>Primeros pasos 
Cuando estén implementados todos los requisitos previos, le interesará completar varias acciones para que se realice la implementación.  Consulte estos tutoriales para empezar:
- [Creación de un inquilino de Windows Virtual Desktop](/azure/virtual-desktop/virtual-desktop-fall-2019/tenant-setup-azure-active-directory)
- [Creación de un grupo de host](/azure/virtual-desktop/create-host-pools-azure-marketplace) con Azure Portal
- [Administración de grupos de aplicaciones](/azure/virtual-desktop/manage-app-groups) para Windows Virtual Desktop

## <a name="eligibility"></a>Elegibilidad
| Nivel de suscripción                                                 |     Canales                                            | Prestación                                                          | ¿Renovable?    |
|--------------------------------------------------------------------|---------------------------------------------------------|------------------------------------------------------------------|---------------|
| Visual Studio Enterprise (estándar)   | Licencia por volumen, Azure, venta directa | Disponible|  Sí          |
| Suscripción de Visual Studio Enterprise con GitHub Enterprise  | VL | Disponible|  Sí          |
| Visual Studio Professional (estándar) | Licencia por volumen, Azure, venta directa                                       | Disponible                                                             |  Sí             |
| Suscripción de Visual Studio Professional con GitHub Enterprise | VL                                       | Disponible                                        |  Sí           |
| Visual Studio Test Professional (estándar)                         | Licencia por volumen, venta directa                                              | Disponible|  Sí          |
| Plataformas MSDN (estándar)                                          | Licencia por volumen, venta directa                                              | Disponible                                         |  Sí          |
| Visual Studio Enterprise (estándar)  | NFR<sup>1</sup> |No disponible  | N/D |
| Visual Studio Enterprise, Visual Studio Professional (de nube mensual) | Azure | No disponible | N/D |

<sup>1</sup> *Incluye No para reventa (NFR), Empleado a tiempo completo (FTE), Profesional mejor valorado (MVP), Director regional (RD), Microsoft Partner Network (MPN), programa Visual Studio Industry Partner (VSIP), Microsoft Certified Trainer, BizSpark, Imagine y NFR básico.*

> [!NOTE]
> Microsoft ya no ofrece suscripciones anuales ni de Visual Studio Professional ni de Visual Studio Enterprise en las suscripciones de nube. Esto no supone cambio alguno en la experiencia actual de los clientes y ni en su capacidad para renovar, aumentar, reducir o cancelar las suscripciones. Conviene que los clientes nuevos vayan a [https://visualstudio.microsoft.com/vs/pricing/](https://visualstudio.microsoft.com/vs/pricing/) para explorar las diferentes opciones de compra de Visual Studio.

¿No sabe con seguridad qué suscripción usa?  Conéctese a [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions?wt.mc_id=o~msft~docs) para ver todas las suscripciones asignadas a su dirección de correo electrónico. Si no ve todas las suscripciones, es posible que haya una o varias asignadas a una dirección de correo electrónico diferente.  Debe iniciar sesión con esa dirección de correo electrónico para ver esas suscripciones.

## <a name="see-also"></a>Vea también
- [Documentación de Azure](/azure/)
- [Documentación sobre Windows Virtual Desktop](/azure/virtual-desktop/)
- [Soporte técnico para suscripciones de Visual Studio](https://my.visualstudio.com/gethelp)

## <a name="next-steps"></a>Pasos siguientes
-   Si tiene que comprar suscripciones de Visual Studio, consulte lo siguiente:
     - [Precios para compras al por menor](https://visualstudio.microsoft.com/vs/pricing/) a través de Microsoft Store
     - [Programas de licencias por volumen](https://www.microsoft.com/licensing/default)
-   Más información sobre [Windows Virtual Desktop](/azure/virtual-desktop/overview)