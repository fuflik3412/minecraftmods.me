import React, { useState } from 'react';
import { Card, CardContent } from '@/components/ui/card';
import { Button } from '@/components/ui/button';

const modsData = {
  horror: [
    {
      title: 'Темні Печери',
      description: 'Моторошна збірка з монстрами та небезпечними підземеллями.',
      downloadLink: '#'
    },
    {
      title: 'Проклятий Ліс',
      description: 'Ліс, з якого не всі повертаються. Спробуй вижити!',
      downloadLink: '#'
    }
  ],
  adventure: [
    {
      title: 'Острів Скарбів',
      description: 'Пригодницька збірка з пошуком скарбів та піратами.',
      downloadLink: '#'
    }
  ],
  tech: [
    {
      title: 'Індустріальний Світ',
      description: 'Технічні моди для автоматизації та побудови фабрик.',
      downloadLink: '#'
    }
  ],
  magic: [
    {
      title: 'Чарівний Реалм',
      description: 'Магічні моди для створення заклять і чарівних предметів.',
      downloadLink: '#'
    }
  ]
};

export default function MinecraftModsSite() {
  const [isAdmin, setIsAdmin] = useState(false);
  const [password, setPassword] = useState('');

  const handleLogin = () => {
    if (password === '25122012') {
      setIsAdmin(true);
    } else {
      alert('Неправильний пароль');
    }
  };

  return (
    <div className="p-4">
      <h1 className="text-3xl font-bold text-center">Minecraft Збірки Модів</h1>
      {!isAdmin ? (
        <div className="mt-4 text-center">
          <input
            type="password"
            placeholder="Введіть пароль для адмін-панелі"
            value={password}
            onChange={(e) => setPassword(e.target.value)}
            className="p-2 border rounded"
          />
          <Button className="ml-2" onClick={handleLogin}>Увійти</Button>
        </div>
      ) : (
        <div className="mt-4 text-center">
          <h2 className="text-2xl">Адмін-панель</h2>
          <p>Тут ти зможеш додавати, редагувати або видаляти збірки.</p>
        </div>
      )}
      <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-4 mt-8">
        {Object.entries(modsData).map(([category, mods]) => (
          <div key={category}>
            <h2 className="text-xl font-semibold capitalize">{category} Збірки</h2>
            {mods.map((mod, index) => (
              <Card key={index} className="mt-2">
                <CardContent>
                  <h3 className="font-bold">{mod.title}</h3>
                  <p>{mod.description}</p>
                  <Button className="mt-2" asChild>
                    <a href={mod.downloadLink}>Завантажити</a>
                  </Button>
                </CardContent>
              </Card>
            ))}
          </div>
        ))}
      </div>
    </div>
  );
}
