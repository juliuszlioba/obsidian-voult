```javascript

import { useCallback, useEffect, useState } from 'react'
import { throttle } from 'radash'

export default function HeaderNav() {
  const [client, setClient] = useState<'none' | 'mobile' | 'desktop'>('none')

  const getVw = useCallback(() => {
    if (typeof window !== 'undefined') {
      const width = window.innerWidth || 0
      if (width >= 1024) return 'desktop'
    }

    return 'mobile'
  }, [])

  useEffect(() => {
    const handleResize = throttle({ interval: 150 }, () => {
      setClient(getVw())
    })
    
    if (typeof window !== 'undefined') {
      window.addEventListener('resize', handleResize)
      return () => {
        window.removeEventListener('resize', handleResize)
      }
    }

    return null
  }, [getVw])

  
  useEffect(() => {
    return setClient(getVw())
    // eslint-disable-next-line react-hooks/exhaustive-deps
  }, [])

...

```