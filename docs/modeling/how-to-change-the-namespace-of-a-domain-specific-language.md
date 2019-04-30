---
title: Procedimiento Cambiar el espacio de nombres de un lenguaje específico de dominio
ms.date: 10/31/2018
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, namespace
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 16fec4cf6150fe0711812d9fabe57fc667e36eef
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993507"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Procedimiento Cambiar el espacio de nombres de un lenguaje específico de dominio

Puede cambiar el espacio de nombres de un lenguaje específico de dominio. Realice el cambio en el **DSL Explorer**, en las propiedades del proyecto de paquete de Dsl y en la información de ensamblado.

## <a name="to-change-the-namespace-of-a-domain-specific-language"></a>Para cambiar el espacio de nombres de un lenguaje específico de dominio

1. En **DSL Explorer**, seleccione el **Dsl** nodo.

2. En el **propiedades** ventana, cambie el **Namespace** propiedad.

3. Guarde la solución y transformar las plantillas.

4. En el **proyecto** menú, elija **Dsl propiedades**.

   Aparecerán las propiedades del proyecto.

5. Seleccione el **aplicación** ficha.

6. Cambiar el **espacio de nombres predeterminado** propiedad para el nuevo nombre de espacio de nombres.

7. Si también desea cambiar el nombre del ensamblado, cambie el **propiedad nombre de ensamblado.**

8. Si ha cambiado el nombre del ensamblado, abra DslPackage\Package.tt y actualice esta línea:

   `string dslAssembly = "YourDSLassembly.Dsl.dll";`

9. Si ha escrito ningún código personalizado, asegúrese de cambiar las referencias de espacio de nombres y clase en los archivos de código.

10. Restablecer la instancia Experimental de Visual Studio.

    1. Eliminar **\Users\\**_{su nombre}_**\AppData\Local\Microsoft\VisualStudio\\\*Exp**.

    2. En el Windows **iniciar** menú, elija **todos los programas** > **Microsoft Visual Studio 2010 SDK** > **herramientas**  >  **Restablecer la instancia Experimental**.

11. En el **compilar** menú, elija **recompilar solución**.

## <a name="see-also"></a>Vea también

[Glosario de las herramientas de lenguajes específicos de dominio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)