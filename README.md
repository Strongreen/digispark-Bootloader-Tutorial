# Tutorial Digispark Bootloader
Recentemente, comprei uma daquelas placas de soquete USB chinesas baratas e descobri que, para usar o IDE do Arduino, você precisa gravar um bootloader nela. Encontrei alguns tutoriais online, mas muitos deles pareciam incompletos ou incluíam etapas redundantes.

Video:

[![View the making of here](https://img.youtube.com/vi/axagDO8AKSI/0.jpg)](https://www.youtube.com/watch?v=axagDO8AKSI)

Veja como gravar um bootloader no digispark usando um Arduino UNO:

1. Instale o Arduino IDE https://www.arduino.cc/en/Main/Software
2. Instale os drivers digistump https://github.com/digistump/DigistumpArduino/releases
3. Abra o IDE do Arduino e vá para arquivo > preferências.
4. Adicione http://digistump.com/package_digistump_index.json aos URLs adicionais do gerenciador de placas.
5. Vá para ferramentas > quadro > gerenciador de quadros.
6. Procure por digistump e instale as placas Digistump AVR.
7. Conecte seu arduino uno via USB.
8. Vá para arquivo > exemplos > 11. ArduinoISP > ArduinoISP para abrir o esboço do ArduinoISP.
9. Aperte o botão de seta para carregá-lo em seu Arduino.
10. Desconecte seu arduino e pegue seu Attiny85, placa de ensaio, alguns fios e um capacitor de 10uF.
11. Conecte o seguinte:

| Digispark pin | Arduino GPIO/Pin |
| --- | --- |
| 1 | 10 |
| 4 | GND |
| 5 | 11 |
| 6 | 12 |
| 7 | 13 |
| 8 | 5V |

Conecte também um capacitor de 10uF entre o arduino RST e o arduino GND. Se estiver usando um capacitor eletrolítico, coloque o ânodo no RST e o cátodo no GND.

12. Conecte seu arduino novamente via USB e entre no IDE do Arduino. Verifique a qual porta ele está conectado. No meu caso é COM3.
13. Edite o arquivo burn_attiny85_bootloader.bat deste repositório (clique com o botão direito e edite). Edite a parte que diz -PCOM22 para corresponder à sua porta. No meu caso, como uso COM3, vou editá-lo para -PCOM3
14. Salve e copie o arquivo bat e t85_default.hex para o diretório de instalação do Arduino.
15. Execute o arquivo bat e agora ele deve gravar o bootloader em seu attiny85.

# Fazendo upload via arduino
Depois de adicionar o bootloader, agora você pode fazer upload via arduino. Há um teste neste repositório se você quiser apenas piscar o LED de depuração.

1. Escreva seu esboço normalmente.
2. Conecte seu attiny à placa de soquete USB. Mas não o conecte ao computador ainda.
3. No IDE do Arduino, escolha Digispark (padrão - 16,5 MHz). Porto não importa.
4. Clique em carregar esboço.
5. Após a compilação, o IDE solicitará que você conecte seu attiny. Faça isso e o esboço será carregado.

Credits & sources:
https://www.youtube.com/watch?v=FI3s4d2I1eQ
https://create.arduino.cc/projecthub/arjun/programming-attiny85-with-arduino-uno-afb829
https://digistump.com/board/index.php?topic=1841.0
