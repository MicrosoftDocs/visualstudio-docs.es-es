---
title: 'Cómo: Cambiar el espacio de nombres de un lenguaje específico del dominio'
description: Proporciona información sobre cómo cambiar el espacio de nombres de un lenguaje específico del dominio.
ms.date: 10/31/2018
ms.topic: how-to
titleSuffix: ''
helpviewer_keywords:
- Domain-Specific Language, namespace
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: db9043c2a4c5abd19c839d2586709412d7607019
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387312"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Cómo: Cambiar el espacio de nombres de un lenguaje específico del dominio

Puede cambiar el espacio de nombres de un lenguaje específico del dominio. Realice el cambio en el **Explorador de DSL**, en las propiedades del proyecto paquete Dsl y en la información del ensamblado.

## <a name="to-change-the-namespace-of-a-domain-specific-language"></a>Para cambiar el espacio de nombres de un lenguaje específico de dominio

1. En **el Explorador de DSL,** seleccione el nodo **Dsl.**

2. En la **ventana Propiedades,** cambie la **propiedad Espacio de** nombres.

3. Guarde la solución y transforme las plantillas.

4. En el **menú Proyecto,** elija **Propiedades de Dsl.**

   Aparecen las propiedades del proyecto.

5. Seleccione la pestaña **Aplicación**.

6. Cambie la **propiedad Espacio de nombres** predeterminado por el nuevo nombre del espacio de nombres.

7. Si también desea cambiar el nombre del ensamblado, cambie la **propiedad Nombre del ensamblado.**

8. Si ha cambiado el nombre del ensamblado, abra DslPackage\Package.tt y actualice esta línea:

   `string dslAssembly = "YourDSLassembly.Dsl.dll";`

9. Si ha escrito código personalizado, asegúrese de cambiar las referencias de clase y espacio de nombres en los archivos de código.

10. Restablezca la Visual Studio experimental.

    1. Elimine **\Users \\**_{your name}_**\AppData\Local\Microsoft\VisualStudio \\ \* Exp**.

    2. En el menú **Inicio de** Windows, elija **Todos** los programas Microsoft Visual Studio herramientas del SDK  >  **de 2010**  >    >  **Restablecer la instancia experimental**.

11. En el menú **Compilar,** elija **Recompilar solución**.

## <a name="see-also"></a>Vea también

[Glosario de herramientas de lenguaje específico del dominio](/previous-versions/bb126564(v=vs.100))