---
title: CA5351 No use algoritmos criptográficos rotos
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 483f51b3-e186-4433-b48e-5ca24a9a9c94
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9c00d4e8ebb385b987bb49a44af8b241883a566b
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45550978"
---
# <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a>CA5351 No use algoritmos criptográficos rotos

|||
|-|-|
|TypeName|DoNotUseBrokenCryptographicAlgorithms|
|Identificador de comprobación|CA5351|
|Categoría|Microsoft.Cryptography|
|Cambio problemático|No trascendental|

> [!NOTE]
> Esta advertencia se actualizó por última vez en noviembre de 2015.

## <a name="cause"></a>Motivo

Las funciones hash como <xref:System.Security.Cryptography.MD5> y los algoritmos de cifrado como <xref:System.Security.Cryptography.DES> y <xref:System.Security.Cryptography.RC2> pueden generar riesgos significativos y provocar la divulgación de información confidencial a través de técnicas de ataque fáciles, como colisiones hash y ataques por fuerza bruta.

La lista de algoritmos criptográficos siguiente está sujeta a ataques criptográficos conocidos. El algoritmo hash criptográfico <xref:System.Security.Cryptography.MD5> está sujeto a ataques de colisión hash.  En función del uso, una colisión hash puede provocar la suplantación, manipulación u otros tipos de ataques en sistemas que se basan en la salida criptográfica única de una función hash. Los algoritmos de cifrado <xref:System.Security.Cryptography.DES> y <xref:System.Security.Cryptography.RC2> están sujetos a ataques criptográficos que pueden provocar la divulgación no intencionada de datos cifrados.

## <a name="rule-description"></a>Descripción de la regla

Los algoritmos criptográficos rotos no se consideran seguros y debe desalentarse su uso. El algoritmo hash MD5 es susceptible a ataques de colisión conocidos, aunque la vulnerabilidad específica variará según el contexto de uso.  Algoritmos hash usados para garantizar la integridad de datos (por ejemplo, la firma de archivo o certificado digital) son especialmente vulnerables.  En este contexto, los atacantes pueden generar dos fragmentos de datos separados, de tal manera que los datos correctos se pueden sustituir por los datos malintencionados, sin cambiar el valor hash ni invalidar una signatura digital asociada.

Para algoritmos de cifrado:

- El cifrado<xref:System.Security.Cryptography.DES> contiene un pequeño tamaño de clave, que podría forzarse en menos de un día.

- El cifrado<xref:System.Security.Cryptography.RC2> es susceptible de sufrir ataques relacionados con la clave, en los que el atacante busca relaciones matemáticas entre todos los valores de clave.

Esta regla se desencadena cuando se encuentra cualquiera de las funciones criptográficas anteriores en el código fuente y emite una advertencia al usuario.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Use opciones de criptografía más segura:

- Para MD5, use valores hash de la [SHA-2](/windows/desktop/SecCrypto/hash-and-signature-algorithms) familia (por ejemplo, <xref:System.Security.Cryptography.SHA512>, <xref:System.Security.Cryptography.SHA384>, <xref:System.Security.Cryptography.SHA256>).

- Para DES y RC2, use el cifrado <xref:System.Security.Cryptography.Aes> .

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

No suprima una advertencia de esta regla a menos que la haya revisado un experto criptográfico.

## <a name="pseudo-code-examples"></a>Ejemplos de pseudocódigo

Los ejemplos de pseudocódigo siguiente muestran el modelo detectado por esta regla y las alternativas posibles.

### <a name="md5-hashing-violation"></a>Infracción de hash MD5

```csharp
using System.Security.Cryptography;
...
var hashAlg = MD5.Create();
```

Solución:

```csharp
using System.Security.Cryptography;
...
var hashAlg = SHA256.Create();
```

### <a name="rc2-encryption-violation"></a>Infracción de cifrado RC2

```csharp
using System.Security.Cryptography;
...
RC2 encAlg = RC2.Create();
```

Solución:

```csharp
using System.Security.Cryptography;
...
using (AesManaged encAlg = new AesManaged())
{
  ...
}
```

### <a name="des-encryption-violation"></a>Infracción de cifrado DES

```csharp
using System.Security.Cryptography;
...
DES encAlg = DES.Create();
```

Solución:

```csharp
using System.Security.Cryptography;
...
using (AesManaged encAlg = new AesManaged())
{
  ...
}
```