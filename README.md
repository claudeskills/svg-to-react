# SVG to React Skill

Skill de Claude para convertir archivos SVG a componentes React/TypeScript con props compatibles con lucide.

## Características

- ⚛️ **Componentes React optimizados**: TypeScript + props estándar
- 📦 **Procesamiento por lotes**: Convierte carpetas enteras
- 🔤 **Naming automático**: PascalCase (logo-icon.svg → LogoIcon.tsx)
- 📋 **Index generado**: Re-exports automáticos para imports limpios
- 🧹 **SVG limpio**: Paths unidos, sin fondos, currentColor
- 🌳 **Tree-shakeable**: Named exports para optimización

## Instalación

1. Descarga `svg-to-react.skill`
2. Abre Claude.ai → Settings → Skills
3. Sube el archivo `.skill`

## Ejemplos de Uso

**Convertir un SVG:**
```
Convierte logo.svg a componente React
```

**Procesar carpeta:**
```
Convierte todos los SVGs en /icons/ a componentes React
```

## API del Componente

Los componentes generados siguen el patrón de lucide y extienden SVGProps:

```typescript
import { SVGProps } from 'react';

interface LogoProps extends SVGProps<SVGSVGElement> {
  size?: number;          // Default: 24
  color?: string;         // Default: "currentColor"
}

export const Logo = ({ 
  size = 24, 
  color = "currentColor",
  className,
  ...rest 
}: LogoProps) => (
  <svg 
    width={size} 
    height={size} 
    className={className}
    viewBox="0 0 24 24"
    {...rest}
  >
    <path fill={color} d="..."/>
  </svg>
);
```

## Ejemplo de Uso

```tsx
import { Logo, UserIcon } from './components';

function App() {
  return (
    <>
      <Logo size={32} color="red" className="mi-icono" />
      <UserIcon size={48} />
    </>
  );
}
```

## Estructura de Salida

**Archivo único:**
```
logo.svg → Logo.tsx
```

**Carpeta (batch):**
```
icons/
├── home.svg
├── user-icon.svg
components/
├── Home.tsx
├── UserIcon.tsx
└── index.ts             # export { Home } from './Home';
```

## Naming

| SVG | Componente |
|-----|------------|
| logo.svg | Logo.tsx |
| user-icon.svg | UserIcon.tsx |
| my_button.svg | MyButton.tsx |

## Ventajas sobre Importar SVGs Directamente

- **Props tipadas**: TypeScript autocompletado
- **Consistencia**: API unificada en todos los iconos
- **Flexibilidad**: Fácil cambiar tamaño/color
- **Tree-shaking**: Solo importa los iconos que uses

## Requisitos

- Claude Desktop o Claude.ai con Skills habilitadas
- Python 3.x (incluido en la skill)

## Licencia

MIT License - Ver archivo LICENSE para detalles

## Autor

Creado por Daniel Serrano para ClaudeSkills
