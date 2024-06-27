---
{"dg-publish":true,"dg-path":"自动控制原理/PID.md","permalink":"/自动控制原理/PID/","dgPassFrontmatter":true,"noteIcon":"","created":"2024-05-21T15:20:27.815+08:00","updated":"2024-06-24T10:40:20.602+08:00"}
---

**PID controller**
**Proportional-Integral-Derivative Controller**

对误差信号 $e(t)$ 进行比例、积分和微分运算变换后形成的控制规律

[[Simulink\|Simulink]]
[[经典环节的传递函数\|经典环节的传递函数]]

<svg xmlns="http://www.w3.org/2000/svg" version="1.1" viewBox="0 0 457.7029089363357 348.1085136559941" width="457.7029089363357" height="348.1085136559941">  <!-- svg-source:excalidraw -->    <defs>    <style class="style-fonts">      @font-face {        font-family: "Virgil";        src: url("https://excalidraw.com/Virgil.woff2");      }      @font-face {        font-family: "Cascadia";        src: url("https://excalidraw.com/Cascadia.woff2");      }      @font-face {        font-family: "Assistant";        src: url("https://excalidraw.com/Assistant-Regular.woff2");      }    </style>      </defs>  <rect x="0" y="0" width="457.7029089363357" height="348.1085136559941" fill="#ffffff"></rect><g stroke-linecap="round" transform="translate(13.197874694155985 142.67527000038976) rotate(0 42.06167696164036 24.711222218309956)"><path d="M12.36 0 C28.43 1.14, 45.18 -0.94, 71.77 0 M12.36 0 C28.35 0.79, 43.18 0.38, 71.77 0 M71.77 0 C79.9 -0.26, 85.05 5.67, 84.12 12.36 M71.77 0 C79.2 1.87, 82.7 2.73, 84.12 12.36 M84.12 12.36 C84.48 17.85, 84.69 28.54, 84.12 37.07 M84.12 12.36 C83.15 20.11, 83.8 27.46, 84.12 37.07 M84.12 37.07 C84.08 44.25, 78.09 48.35, 71.77 49.42 M84.12 37.07 C85.5 45.7, 80.82 47.69, 71.77 49.42 M71.77 49.42 C57.81 50.82, 39.97 50.21, 12.36 49.42 M71.77 49.42 C53.26 49.46, 34.3 49.07, 12.36 49.42 M12.36 49.42 C5.69 48.19, 0.25 45.25, 0 37.07 M12.36 49.42 C2.24 51.3, 1.24 43.63, 0 37.07 M0 37.07 C-0.35 30.1, 1.57 20.35, 0 12.36 M0 37.07 C0.41 29.18, 0.7 20.19, 0 12.36 M0 12.36 C1.63 4.21, 2.8 0.04, 12.36 0 M0 12.36 C1.26 6.18, 3.97 0.48, 12.36 0" stroke="#1e1e1e" stroke-width="2" fill="none"></path></g><g transform="translate(29.400176655796315 155.38649221869971) rotate(0 25.859375 12)"><text x="25.859375" y="19.3125" font-family="Cascadia, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="middle" style="white-space: pre;" direction="ltr" dominant-baseline="alphabetic">P比例</text></g><g stroke-linecap="round" transform="translate(10 58.66720760185112) rotate(0 43.208966709249935 19.29452277638123)"><path d="M9.65 0 C23.09 -0.24, 38.56 0.04, 76.77 0 M9.65 0 C36.59 -0.36, 62.22 -0.39, 76.77 0 M76.77 0 C83.94 0.53, 87.93 4.2, 86.42 9.65 M76.77 0 C83.79 1.49, 86.86 4.28, 86.42 9.65 M86.42 9.65 C86.9 14.33, 85.24 19.68, 86.42 28.94 M86.42 9.65 C87.21 15.53, 85.55 22.27, 86.42 28.94 M86.42 28.94 C86.63 35.77, 81.48 39.02, 76.77 38.59 M86.42 28.94 C85.96 36.1, 85.44 39.17, 76.77 38.59 M76.77 38.59 C63.6 38.39, 46.7 39.04, 9.65 38.59 M76.77 38.59 C52.21 39.13, 27.41 37.98, 9.65 38.59 M9.65 38.59 C2.38 37.45, 0.36 35.34, 0 28.94 M9.65 38.59 C3.74 37.03, 0.49 34.65, 0 28.94 M0 28.94 C-0.75 25.18, 1.05 19.84, 0 9.65 M0 28.94 C0.64 21.72, -0.58 14.12, 0 9.65 M0 9.65 C0.36 2.43, 4.03 0.5, 9.65 0 M0 9.65 C1.3 1.1, 2.67 0.68, 9.65 0" stroke="#1e1e1e" stroke-width="2" fill="none"></path></g><g transform="translate(27.34959170924992 65.96173037823232) rotate(0 25.859375 12)"><text x="25.859375" y="19.3125" font-family="Cascadia, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="middle" style="white-space: pre;" direction="ltr" dominant-baseline="alphabetic">I积分</text></g><g stroke-linecap="round" transform="translate(15.954305794582751 243.51392881394483) rotate(0 42.92212063949839 19.437926904977672)"><path d="M9.72 0 C27.03 0.61, 47.56 -0.39, 76.13 0 M9.72 0 C31.51 -1.16, 55.11 -0.83, 76.13 0 M76.13 0 C82.06 -1.6, 86.11 4.66, 85.84 9.72 M76.13 0 C83.55 0.54, 84.46 5.19, 85.84 9.72 M85.84 9.72 C85.27 14.51, 85.49 18.47, 85.84 29.16 M85.84 9.72 C86.47 15.56, 86.09 22.61, 85.84 29.16 M85.84 29.16 C86.15 36.98, 81.54 39.79, 76.13 38.88 M85.84 29.16 C84.51 36.64, 83.4 40.65, 76.13 38.88 M76.13 38.88 C54.36 40.04, 36.52 37.22, 9.72 38.88 M76.13 38.88 C60.18 38.81, 42.93 38.63, 9.72 38.88 M9.72 38.88 C4.71 38.17, -1.58 34.05, 0 29.16 M9.72 38.88 C2.59 37.45, 0.26 35.35, 0 29.16 M0 29.16 C-0.54 22.3, -1.32 14.67, 0 9.72 M0 29.16 C-0.22 24.56, -0.44 21.67, 0 9.72 M0 9.72 C-0.54 5.12, 1.64 -1.71, 9.72 0 M0 9.72 C0.14 5.03, 4.92 1.28, 9.72 0" stroke="#1e1e1e" stroke-width="2" fill="none"></path></g><g transform="translate(33.01705143408111 250.95185571892247) rotate(0 25.859375 12)"><text x="25.859375" y="19.3125" font-family="Cascadia, Segoe UI Emoji" font-size="20px" fill="#1e1e1e" text-anchor="middle" style="white-space: pre;" direction="ltr" dominant-baseline="alphabetic">D微分</text></g><g stroke-linecap="round" transform="translate(301.74110439392865 10) rotate(0 42.06167696164036 24.711222218309956)"><path d="M12.36 0 C34.43 1.4, 54.73 2.17, 71.77 0 M12.36 0 C31.66 -0.62, 50.19 0.21, 71.77 0 M71.77 0 C79.24 -1.61, 85.17 4.48, 84.12 12.36 M71.77 0 C78.46 1.76, 86.16 4.6, 84.12 12.36 M84.12 12.36 C82.69 21.13, 85.92 26.29, 84.12 37.07 M84.12 12.36 C84.56 22.34, 85.03 30.6, 84.12 37.07 M84.12 37.07 C84.28 45.23, 80.49 51.37, 71.77 49.42 M84.12 37.07 C83.17 44.63, 78.05 49.12, 71.77 49.42 M71.77 49.42 C59.91 48.1, 44.75 48.63, 12.36 49.42 M71.77 49.42 C55.66 49.54, 37.65 49.88, 12.36 49.42 M12.36 49.42 C5.09 47.53, -1.44 44.15, 0 37.07 M12.36 49.42 C2.12 49.2, -0.53 44.63, 0 37.07 M0 37.07 C1.51 27.1, -0.42 21.4, 0 12.36 M0 37.07 C0.28 30.72, -1 25.97, 0 12.36 M0 12.36 C1.56 5.36, 2.25 0.95, 12.36 0 M0 12.36 C-2.18 2.87, 5.55 0.7, 12.36 0" stroke="#1971c2" stroke-width="2" fill="none"></path></g><g transform="translate(332.084031355569 22.711222218309956) rotate(0 11.71875 12)"><text x="11.71875" y="19.3125" font-family="Cascadia, Segoe UI Emoji" font-size="20px" fill="#1971c2" text-anchor="middle" style="white-space: pre;" direction="ltr" dominant-baseline="alphabetic">PI</text></g><g stroke-linecap="round" transform="translate(310.14630321203344 288.6860692193742) rotate(0 42.06167696164036 24.711222218309956)"><path d="M12.36 0 C29.4 -0.45, 50.59 -0.5, 71.77 0 M12.36 0 C24.98 0.53, 37.42 0.26, 71.77 0 M71.77 0 C78.42 -1, 84.44 5.52, 84.12 12.36 M71.77 0 C81.13 0.86, 86.2 6.14, 84.12 12.36 M84.12 12.36 C83.97 18.38, 82.13 27.2, 84.12 37.07 M84.12 12.36 C84 18.31, 84.76 23.47, 84.12 37.07 M84.12 37.07 C85.78 43.6, 78.03 50.4, 71.77 49.42 M84.12 37.07 C84.62 43.76, 81.63 49.54, 71.77 49.42 M71.77 49.42 C53.19 49.43, 32.22 50.37, 12.36 49.42 M71.77 49.42 C51.62 50.48, 29.64 49.91, 12.36 49.42 M12.36 49.42 C5.21 49.51, -1.48 45.09, 0 37.07 M12.36 49.42 C3.99 51.31, 1.06 44.59, 0 37.07 M0 37.07 C-0.26 29.85, -0.38 26.81, 0 12.36 M0 37.07 C1.03 27.92, 0.06 21.48, 0 12.36 M0 12.36 C-0.25 3.54, 3.23 -1.51, 12.36 0 M0 12.36 C1.88 4.43, 4.43 -1.83, 12.36 0" stroke="#2f9e44" stroke-width="2" fill="none"></path></g><g transform="translate(340.4892301736738 301.3972914376841) rotate(0 11.71875 12.000000000000028)"><text x="11.71875" y="19.3125" font-family="Cascadia, Segoe UI Emoji" font-size="20px" fill="#2f9e44" text-anchor="middle" style="white-space: pre;" direction="ltr" dominant-baseline="alphabetic">PD</text></g><g stroke-linecap="round" transform="translate(363.579555013055 145.40394669998906) rotate(0 42.06167696164036 24.711222218309956)"><path d="M12.36 0 C27.64 2.47, 45.33 -1, 71.77 0 M12.36 0 C30 0.77, 47.8 -0.44, 71.77 0 M71.77 0 C80.07 0.47, 85.32 2.2, 84.12 12.36 M71.77 0 C79.39 1.07, 85.41 5.63, 84.12 12.36 M84.12 12.36 C84.77 19.24, 82.56 31.98, 84.12 37.07 M84.12 12.36 C83.44 17.24, 84.22 22.24, 84.12 37.07 M84.12 37.07 C82.68 44.85, 80.05 47.75, 71.77 49.42 M84.12 37.07 C86.22 47.6, 82.07 48.67, 71.77 49.42 M71.77 49.42 C52.46 49.48, 32.2 49.52, 12.36 49.42 M71.77 49.42 C50.47 49.41, 27.46 48.96, 12.36 49.42 M12.36 49.42 C3.14 49, -1.17 45.33, 0 37.07 M12.36 49.42 C5.13 50.52, 0.93 43.64, 0 37.07 M0 37.07 C-0.56 29.35, -0.59 18.09, 0 12.36 M0 37.07 C-0.04 29.38, 0.4 21.69, 0 12.36 M0 12.36 C1.86 6.05, 4.42 -0.86, 12.36 0 M0 12.36 C-1.82 2.53, 6.05 1.05, 12.36 0" stroke="#e03131" stroke-width="2" fill="none"></path></g><g transform="translate(388.06310697469536 158.11516891829902) rotate(0 17.578125 12)"><text x="17.578125" y="19.3125" font-family="Cascadia, Segoe UI Emoji" font-size="20px" fill="#e03131" text-anchor="middle" style="white-space: pre;" direction="ltr" dominant-baseline="alphabetic">PID</text></g><g stroke-linecap="round"><g transform="translate(98.46838735221195 68.89253850085024) rotate(0 99.85474574214258 -23.92322517317757)"><path d="M0 0 C59.64 -14.49, 118.71 -26.6, 199.71 -47.85 M0 0 C47.94 -10.68, 96.2 -20.93, 199.71 -47.85" stroke="#1971c2" stroke-width="2" fill="none"></path></g><g transform="translate(98.46838735221195 68.89253850085024) rotate(0 99.85474574214258 -23.92322517317757)"><path d="M179.03 -33.79 C186.28 -38.22, 193.02 -40.21, 199.71 -47.85 M179.03 -33.79 C183.39 -37.87, 188.21 -39.76, 199.71 -47.85" stroke="#1971c2" stroke-width="2" fill="none"></path></g><g transform="translate(98.46838735221195 68.89253850085024) rotate(0 99.85474574214258 -23.92322517317757)"><path d="M174.84 -50.37 C183.25 -49.95, 191.22 -47.09, 199.71 -47.85 M174.84 -50.37 C180.15 -50.39, 185.99 -48.26, 199.71 -47.85" stroke="#1971c2" stroke-width="2" fill="none"></path></g></g><mask></mask><g stroke-linecap="round"><g transform="translate(98.60446140650197 166.14942062468677) rotate(0 100.20957212020119 -67.41590924885296)"><path d="M0 0 C66.83 -45.2, 132.27 -88.94, 200.42 -134.83 M0 0 C72.17 -47.4, 144.09 -95.61, 200.42 -134.83" stroke="#1971c2" stroke-width="2" fill="none"></path></g><g transform="translate(98.60446140650197 166.14942062468677) rotate(0 100.20957212020119 -67.41590924885296)"><path d="M185.9 -114.48 C191.16 -123.09, 195.02 -128.86, 200.42 -134.83 M185.9 -114.48 C191.66 -121.47, 196.91 -128.59, 200.42 -134.83" stroke="#1971c2" stroke-width="2" fill="none"></path></g><g transform="translate(98.60446140650197 166.14942062468677) rotate(0 100.20957212020119 -67.41590924885296)"><path d="M176.22 -128.57 C184.64 -132.47, 191.7 -133.58, 200.42 -134.83 M176.22 -128.57 C185.48 -130.46, 194.2 -132.53, 200.42 -134.83" stroke="#1971c2" stroke-width="2" fill="none"></path></g></g><mask></mask><g stroke-linecap="round"><g transform="translate(98.3212286174367 173.48480991203522) rotate(0 105.41253729729836 70.84845210224182)"><path d="M0 0 C68.25 44.63, 139.17 90.83, 210.83 141.7 M0 0 C81.49 53.91, 163.5 108.7, 210.83 141.7" stroke="#2f9e44" stroke-width="2" fill="none"></path></g><g transform="translate(98.3212286174367 173.48480991203522) rotate(0 105.41253729729836 70.84845210224182)"><path d="M186.61 135.47 C193.3 136.51, 203.48 138.25, 210.83 141.7 M186.61 135.47 C195.77 138.03, 205.57 140.32, 210.83 141.7" stroke="#2f9e44" stroke-width="2" fill="none"></path></g><g transform="translate(98.3212286174367 173.48480991203522) rotate(0 105.41253729729836 70.84845210224182)"><path d="M196.28 121.36 C199.82 127.09, 206.83 133.45, 210.83 141.7 M196.28 121.36 C201.7 129.46, 207.74 137.21, 210.83 141.7" stroke="#2f9e44" stroke-width="2" fill="none"></path></g></g><mask></mask><g stroke-linecap="round"><g transform="translate(102.79854707357953 278.903539616108) rotate(0 102.58628595902007 21.464111534469794)"><path d="M0 0 C54.55 12.54, 108.36 24.72, 205.17 42.93 M0 0 C46.64 8.83, 93.48 19.9, 205.17 42.93" stroke="#2f9e44" stroke-width="2" fill="none"></path></g><g transform="translate(102.79854707357953 278.903539616108) rotate(0 102.58628595902007 21.464111534469794)"><path d="M180.43 46.48 C187.21 45.45, 193.23 45.45, 205.17 42.93 M180.43 46.48 C185.83 44.76, 191.71 45.45, 205.17 42.93" stroke="#2f9e44" stroke-width="2" fill="none"></path></g><g transform="translate(102.79854707357953 278.903539616108) rotate(0 102.58628595902007 21.464111534469794)"><path d="M183.93 29.74 C189.82 33.12, 194.91 37.54, 205.17 42.93 M183.93 29.74 C188.63 31.83, 193.71 36.32, 205.17 42.93" stroke="#2f9e44" stroke-width="2" fill="none"></path></g></g><mask></mask><g stroke-linecap="round"><g transform="translate(98.60803687462959 167.26138079983278) rotate(0 130.9729202525701 0.7807552068360337)"><path d="M0 0 C89.28 -2.1, 175.38 -1.81, 261.95 1.56 M0 0 C94.55 -0.93, 191.18 -0.2, 261.95 1.56" stroke="#e03131" stroke-width="2" fill="none"></path></g><g transform="translate(98.60803687462959 167.26138079983278) rotate(0 130.9729202525701 0.7807552068360337)"><path d="M238.3 9.68 C248 5.85, 253.77 2.85, 261.95 1.56 M238.3 9.68 C246.08 6.67, 256.39 3.91, 261.95 1.56" stroke="#e03131" stroke-width="2" fill="none"></path></g><g transform="translate(98.60803687462959 167.26138079983278) rotate(0 130.9729202525701 0.7807552068360337)"><path d="M238.62 -7.42 C248.32 -5.51, 253.99 -2.79, 261.95 1.56 M238.62 -7.42 C246.13 -4.2, 256.32 -0.74, 261.95 1.56" stroke="#e03131" stroke-width="2" fill="none"></path></g></g><mask></mask><g stroke-linecap="round"><g transform="translate(100.18927470792812 75.73314626521116) rotate(0 130.13757535242752 46.80981440248371)"><path d="M0 0 C52.01 18.95, 106.81 40.33, 260.28 93.62 M0 0 C78.69 27.73, 158.31 55.12, 260.28 93.62" stroke="#e03131" stroke-width="2" fill="none"></path></g><g transform="translate(100.18927470792812 75.73314626521116) rotate(0 130.13757535242752 46.80981440248371)"><path d="M235.28 93.48 C239.39 92.01, 246.5 94.92, 260.28 93.62 M235.28 93.48 C242.49 94.13, 251.34 93.02, 260.28 93.62" stroke="#e03131" stroke-width="2" fill="none"></path></g><g transform="translate(100.18927470792812 75.73314626521116) rotate(0 130.13757535242752 46.80981440248371)"><path d="M241.21 77.44 C244.01 79.22, 249.91 85.41, 260.28 93.62 M241.21 77.44 C246.71 82.98, 253.76 86.71, 260.28 93.62" stroke="#e03131" stroke-width="2" fill="none"></path></g></g><mask></mask><g stroke-linecap="round"><g transform="translate(102.79854707357953 267.81174565551794) rotate(0 128.85682419547703 -46.45305613089212)"><path d="M0 0 C79.74 -29.06, 159.4 -57.67, 257.71 -92.91 M0 0 C100.55 -37.06, 199.67 -73.38, 257.71 -92.91" stroke="#e03131" stroke-width="2" fill="none"></path></g><g transform="translate(102.79854707357953 267.81174565551794) rotate(0 128.85682419547703 -46.45305613089212)"><path d="M238.34 -77.11 C244.32 -82.34, 249.83 -86.93, 257.71 -92.91 M238.34 -77.11 C246.57 -83.65, 253.31 -90.26, 257.71 -92.91" stroke="#e03131" stroke-width="2" fill="none"></path></g><g transform="translate(102.79854707357953 267.81174565551794) rotate(0 128.85682419547703 -46.45305613089212)"><path d="M232.72 -93.26 C240.52 -93.47, 247.78 -93.04, 257.71 -92.91 M232.72 -93.26 C243.05 -93.58, 251.97 -93.94, 257.71 -92.91" stroke="#e03131" stroke-width="2" fill="none"></path></g></g><mask></mask></svg>

### P 比例
>输出与误差信号成比例

$$\begin{align}
G_{c}(s)=K_{p}
\end{align}$$

提高系统的开环增益，减小系统[[线性系统稳态误差计算\|稳态误差]]

### I 积分
>输出与误差信号随时间的积分成比例

$$\begin{align}
G_{c}(s)= \dfrac{1}{T_{i}s}
\end{align}$$

积分的累积作用，**不单独使用**
- 提高系统型别，减小稳态误差
- 相角滞后，可能使系统不稳定

### D 微分
>输出与误差信号的变化率成比例

$$\begin{align}
G_{c}(s)=T_{d}s
\end{align}$$

对噪声敏感，一般**不单独使用**


### PD 比例微分
**[[超前校正\|超前校正]]**

$$\begin{align}
G_{c}(s)=K_{p}(1+T_{d}s)
\end{align}$$



增加开环零点
[[经典环节的传递函数\|经典环节的传递函数]]

对高频信号的抑制能力减弱


### PI 比例积分
**[[滞后校正\|滞后校正]]**

$$\begin{align}
G_{c}(s)&=K_{p}(1+ \dfrac{1}{T_{i}s}) \\
&= \dfrac{K_{p}(s+\dfrac{1}{T_{i}})}{s}
\end{align}$$

PI控制器相当于增加了一个位于原点的开环极点和一个负实开环零点 
开环极点可以提高型别，减小系统稳态误差 
开环零点可以改善缓和极点对系统稳定性及动态过程产生的不利影响 
增加Ti值，削弱对稳定性的不利影响
改善中频段，提升截止频率，改善动态性能

### PID

$$\begin{align}
G_{c}(s)&=K_{p}(1+ \dfrac{1}{T_{i}s}+ T_{d}s) \\
&=\dfrac{K_{p}}{T_{i}} \dfrac{T_{i}T_{d}s^{2}+T_{i}s+1}{s}
\end{align}$$

低频段


中频段



### PID 校正
一般不能单独使用 D（按偏差控制，系统不稳定）, I (误差累积)

- 数学模型已知及大多数数学模型难以确定的控制系统或过程 
- PID 控制参数整定方便，结构灵活 
- 数字 PID 控制越来越普及