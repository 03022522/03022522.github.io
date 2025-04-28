---
permalink: /
title: "Academic Pages is a ready-to-fork GitHub Pages template for academic personal websites"
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---
<!DOCTYPE html>
<html>
<head>
    <title>我的像素小窝</title>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link href="https://fonts.googleapis.com/css2?family=Press+Start+2P&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="pixel-frame">
        <h1>我的像素日记</h1>
        <div class="pixel-box">
            <p>今天打败了最终BOSS！🎮</p>
        </div>
    </div>
    <script src="script.js"></script>
</body>
</html>my-pixel-site/
├── index.html       # 主页面
├── style.css        # 样式文件
├── script.js        # JavaScript文件
├── assets/          # 资源文件夹
│   ├── images/      # 存放图片
│   ├── fonts/       # 存放像素字体
<!DOCTYPE html>
<html lang="zh">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>我的像素小窝</title>
    <link href="https://fonts.googleapis.com/css2?family=Press+Start+2P&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="pixel-frame">
        <!-- 导航栏 -->
        <nav class="pixel-nav">
            <button class="pixel-btn active" data-page="home">🏠 主页</button>
            <button class="pixel-btn" data-page="photos">📷 照片墙</button>
            <button class="pixel-btn" data-page="notes">📝 随笔</button>
            <button class="pixel-btn" data-page="diary">📅 日记</button>
            <button class="pixel-btn" data-page="todo">✅ 待办</button>
        </nav>
        
        <!-- 主内容区 -->
        <main class="pixel-content">
            <!-- 默认显示主页 -->
            <section id="home-page" class="page active">
                <h1 class="pixel-title">欢迎来到我的像素小窝</h1>
                <div class="pixel-avatar">(≧∇≦)ﾉ</div>
                <p class="pixel-text">这里存放着我喜欢的一切...</p>
            </section>
            
            <!-- 照片墙页面 -->
            <section id="photos-page" class="page">
                <h2 class="pixel-subtitle">我的照片墙</h2>
                <div class="photo-grid"></div>
            </section>
            
            <!-- 其他页面... -->
        </main>
        
        <!-- 页脚 -->
        <footer class="pixel-footer">
            <div class="pixel-scroll">❤️ 制作于2023 ❤️</div>
        </footer>
    </div>
    
    <!-- 浮动像素元素 -->
    <div class="pixel-floating">★</div>
    <div class="pixel-floating">♥</div>
    
    <script src="script.js"></script>
</body>
</html>/* 基础样式 */
* {
    box-sizing: border-box;
    image-rendering: pixelated;
}

body {
    background-color: #e0f8f8;
    font-family: 'Press Start 2P', cursive;
    line-height: 1.6;
    margin: 0;
    padding: 20px;
    overflow-x: hidden;
}

/* 像素框架 */
.pixel-frame {
    max-width: 900px;
    margin: 0 auto;
    border: 4px solid #000;
    background-color: #9cbd8f;
    padding: 20px;
    box-shadow: 8px 8px 0 #000;
    position: relative;
}

/* 导航栏 */
.pixel-nav {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    margin-bottom: 20px;
    border-bottom: 3px solid #000;
    padding-bottom: 15px;
}

/* 像素按钮 */
.pixel-btn {
    background: #ff6b6b;
    border: 3px solid #000;
    padding: 8px 16px;
    font-family: inherit;
    cursor: pointer;
    font-size: 12px;
    transition: all 0.2s;
}

.pixel-btn:hover {
    background: #ff8e8e;
    transform: translate(2px, 2px);
}

.pixel-btn.active {
    background: #4d96ff;
    color: white;
}

/* 页面内容 */
.page {
    display: none;
    min-height: 400px;
}

.page.active {
    display: block;
}

/* 照片墙网格 */
.photo-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(100px, 1fr));
    gap: 10px;
}

.photo-item {
    width: 100%;
    aspect-ratio: 1;
    background-color: #fff;
    border: 3px solid #000;
    overflow: hidden;
}

.photo-item img {
    width: 100%;
    height: 100%;
    object-fit: cover;
}

/* 浮动像素元素 */
.pixel-floating {
    position: fixed;
    font-size: 24px;
    animation: float 5s infinite ease-in-out;
    z-index: -1;
    opacity: 0.7;
}

@keyframes float {
    0%, 100% { transform: translateY(0) rotate(0deg); }
    50% { transform: translateY(-20px) rotate(5deg); }
}

/* 响应式设计 */
@media (max-width: 600px) {
    .pixel-nav {
        flex-direction: column;
    }
    
    .pixel-btn {
        width: 100%;
    }
}// 页面切换功能
document.querySelectorAll('.pixel-btn').forEach(btn => {
    btn.addEventListener('click', () => {
        // 移除所有按钮的active类
        document.querySelectorAll('.pixel-btn').forEach(b => b.classList.remove('active'));
        // 给当前按钮添加active类
        btn.classList.add('active');
        
        // 隐藏所有页面
        document.querySelectorAll('.page').forEach(page => page.classList.remove('active'));
        // 显示对应页面
        const pageId = btn.getAttribute('data-page') + '-page';
        document.getElementById(pageId).classList.add('active');
    });
});

// 照片墙功能
const photoGrid = document.querySelector('.photo-grid');
const samplePhotos = [
    'assets/images/photo1.jpg',
    'assets/images/photo2.jpg',
    // 添加更多照片路径
];

// 创建照片元素
samplePhotos.forEach(photo => {
    const photoItem = document.createElement('div');
    photoItem.className = 'photo-item';
    
    const img = document.createElement('img');
    img.src = photo;
    img.alt = '我的照片';
    
    photoItem.appendChild(img);
    photoGrid.appendChild(photoItem);
});

// 创建随机浮动像素元素
function createFloatingPixel() {
    const pixels = ['★', '♥', '♫', '☀', '☁', '♣', '♦'];
    const pixel = document.createElement('div');
    pixel.className = 'pixel-floating';
    pixel.textContent = pixels[Math.floor(Math.random() * pixels.length)];
    pixel.style.left = Math.random() * 100 + 'vw';
    pixel.style.top = Math.random() * 100 + 'vh';
    pixel.style.animationDuration = (3 + Math.random() * 7) + 's';
    pixel.style.fontSize = (16 + Math.random() * 32) + 'px';
    document.body.appendChild(pixel);
}

// 创建5个浮动元素
for (let i = 0; i < 5; i++) {
    createFloatingPixel();
}<section id="todo-page" class="page">
    <h2 class="pixel-subtitle">待办事项</h2>
    <div class="todo-container">
        <input type="text" id="new-todo" class="pixel-input" placeholder="添加新任务...">
        <button id="add-todo" class="pixel-btn">添加</button>
        <div class="todo-list"></div>
    </div>
</section>.todo-container {
    margin-top: 20px;
}

.pixel-input {
    border: 3px solid #000;
    padding: 8px;
    font-family: inherit;
    margin-right: 10px;
    width: 200px;
}

.todo-list {
    margin-top: 20px;
}

.todo-item {
    display: flex;
    align-items: center;
    margin-bottom: 10px;
    background: #fff;
    padding: 10px;
    border: 3px solid #000;
}

.todo-checkbox {
    width: 20px;
    height: 20px;
    border: 3px solid #000;
    margin-right: 10px;
    cursor: pointer;
    position: relative;
}

.todo-checkbox.checked::after {
    content: '✓';
    position: absolute;
    top: -5px;
    left: 2px;
}

.todo-text {
    flex-grow: 1;
}

.delete-todo {
    background: #ff0000;
    color: white;
    border: none;
    width: 20px;
    height: 20px;
    cursor: pointer;
}// 待办事项功能
const todoList = document.querySelector('.todo-list');
const newTodoInput = document.getElementById('new-todo');
const addTodoBtn = document.getElementById('add-todo');

function addTodoItem(text) {
    const todoItem = document.createElement('div');
    todoItem.className = 'todo-item';
    
    const checkbox = document.createElement('div');
    checkbox.className = 'todo-checkbox';
    
    const todoText = document.createElement('span');
    todoText.className = 'todo-text';
    todoText.textContent = text;
    
    const deleteBtn = document.createElement('button');
    deleteBtn.className = 'delete-todo pixel-btn';
    deleteBtn.textContent = 'X';
    
    checkbox.addEventListener('click', () => {
        checkbox.classList.toggle('checked');
        todoText.style.textDecoration = checkbox.classList.contains('checked') ? 'line-through' : 'none';
    });
    
    deleteBtn.addEventListener('click', () => {
        todoItem.remove();
    });
    
    todoItem.appendChild(checkbox);
    todoItem.appendChild(todoText);
    todoItem.appendChild(deleteBtn);
    todoList.appendChild(todoItem);
}

addTodoBtn.addEventListener('click', () => {
    if (newTodoInput.value.trim() !== '') {
        addTodoItem(newTodoInput.value.trim());
        newTodoInput.value = '';
    }
});

newTodoInput.addEventListener('keypress', (e) => {
    if (e.key === 'Enter' && newTodoInput.value.trim() !== '') {
        addTodoItem(newTodoInput.value.trim());
        newTodoInput.value = '';
    }
});
