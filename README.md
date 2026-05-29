<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>The Creative Story Wall</title>

<style>
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  font-family: Georgia, serif;
  background: linear-gradient(135deg, #fff1eb, #ace0f9);
  color: #2b2b2b;
}

header {
  text-align: center;
  padding: 70px 20px;
  background: linear-gradient(120deg, #ff9a9e, #fad0c4, #fad390);
  color: #3b1f2b;
}

header h1 {
  font-size: 3rem;
  margin-bottom: 10px;
}

header p {
  font-size: 1.2rem;
}

nav {
  background: #3b1f2b;
  text-align: center;
  padding: 15px;
}

nav a {
  color: white;
  margin: 0 15px;
  text-decoration: none;
  font-weight: bold;
}

nav a:hover {
  color: #fad390;
}

.container {
  max-width: 1000px;
  margin: 40px auto;
  padding: 20px;
}

.intro,
.story-form,
.story-card {
  background: white;
  padding: 30px;
  border-radius: 20px;
  box-shadow: 0 8px 20px rgba(0,0,0,0.15);
}

.intro {
  text-align: center;
  margin-bottom: 30px;
}

.story-form {
  background: #ffffffcc;
  margin-bottom: 30px;
}

.story-form h2,
.story-card h3 {
  color: #9b2c6f;
}

label {
  font-weight: bold;
  color: #9b2c6f;
  display: block;
  margin-top: 12px;
}

input,
textarea {
  width: 100%;
  padding: 14px;
  margin: 10px 0;
  border: 2px solid #f3a6c8;
  border-radius: 12px;
  font-size: 1rem;
  font-family: Georgia, serif;
}

textarea {
  height: 150px;
  resize: vertical;
}

button {
  background: #9b2c6f;
  color: white;
  border: none;
  padding: 12px 22px;
  border-radius: 30px;
  cursor: pointer;
  font-size: 1rem;
  margin-top: 10px;
}

button:hover {
  background: #5f1844;
}

.stories {
  display: grid;
  gap: 20px;
}

.story-card {
  border-left: 8px solid #ff9a9e;
}

.story-card small {
  color: #777;
}

.artist-info {
  display: flex;
  align-items: center;
  gap: 15px;
}

.artist-photo {
  width: 70px;
  height: 70px;
  border-radius: 50%;
  object-fit: cover;
  border: 3px solid #f3a6c8;
}

.art-photo {
  width: 100%;
  max-height: 350px;
  object-fit: cover;
  border-radius: 15px;
  margin: 20px 0;
}

.like-btn {
  margin-top: 15px;
}

.reply-box {
  margin-top: 20px;
  padding-top: 15px;
  border-top: 1px solid #eee;
}

.reply-box textarea {
  height: 90px;
}

.reply {
  background: #fff4fa;
  padding: 12px;
  margin-top: 12px;
  border-radius: 12px;
  border-left: 4px solid #9b2c6f;
}

.reply strong {
  color: #9b2c6f;
}

footer {
  text-align: center;
  padding: 25px;
  background: #3b1f2b;
  color: white;
  margin-top: 40px;
}

@media (max-width: 600px) {
  header h1 {
    font-size: 2.2rem;
  }

  nav a {
    display: block;
    margin: 10px 0;
  }

  .artist-info {
    flex-direction: column;
    align-items: flex-start;
  }
}
</style>
</head>

<body>

<header>
  <h1>The Creative Story Wall</h1>
  <p>A place where artists share their journey, inspiration, and dreams.</p>
</header>

<nav>
  <a href="#">Home</a>
  <a href="#">Stories</a>
  <a href="#">Artists</a>
  <a href="#">Contact</a>
</nav>

<div class="container">

  <section class="intro">
    <h2>Share Your Art Story</h2>
    <p>
      Every artist has a beginning. Share your creative journey,
      your favorite medium, what inspires you, or what art means to you.
    </p>
  </section>

  <section class="story-form">
    <h2>Post Your Story</h2>

    <label for="name">Artist Name</label>
    <input type="text" id="name" placeholder="Your name or artist name">

    <label for="title">Story Title</label>
    <input type="text" id="title" placeholder="Story title">

    <label for="artistPhoto">Artist Photo</label>
    <input type="file" id="artistPhoto" accept="image/*">

    <label for="artPhoto">Artwork Photo</label>
    <input type="file" id="artPhoto" accept="image/*">

    <label for="story">Your Story</label>
    <textarea id="story" placeholder="Write your art story here..."></textarea>

    <button onclick="postStory()">Post Story</button>
  </section>

  <section class="stories" id="stories">

    <div class="story-card">
      <div class="artist-info">
        <img
          src="https://via.placeholder.com/150"
          alt="Artist placeholder"
          class="artist-photo"
        >

        <div>
          <h3>Welcome to the Story Wall</h3>
          <small>Posted by The Artist Community</small>
        </div>
      </div>

      <p>
        This is where artists can share their stories. Add your own post above
        and watch it appear here.
      </p>

      <button class="like-btn" onclick="likeStory(this)">
        ❤️ Like <span>0</span>
      </button>

      <div class="reply-box">
        <input type="text" placeholder="Your name" class="reply-name">
        <textarea placeholder="Write a response..." class="reply-text"></textarea>
        <button onclick="addReply(this)">Reply</button>
      </div>

      <div class="replies"></div>
    </div>

  </section>

</div>

<footer>
  <p>&copy; 2026 The Creative Story Wall | Made for artists and dreamers</p>
</footer>

<script>
function postStory() {
  let name = document.getElementById("name").value;
  let title = document.getElementById("title").value;
  let story = document.getElementById("story").value;
  let artistPhoto = document.getElementById("artistPhoto").files[0];
  let artPhoto = document.getElementById("artPhoto").files[0];

  if (name === "" || title === "" || story === "") {
    alert("Please fill out your name, title, and story.");
    return;
  }

  let artistImage = "";
  let artImage = "";

  if (artistPhoto) {
    let artistReader = new FileReader();

    artistReader.onload = function(e) {
      artistImage = e.target.result;

      if (artPhoto) {
        let artReader = new FileReader();

        artReader.onload = function(event) {
          artImage = event.target.result;
          createStoryCard(name, title, story, artistImage, artImage);
        };

        artReader.readAsDataURL(artPhoto);
      } else {
        createStoryCard(name, title, story, artistImage, artImage);
      }
    };

    artistReader.readAsDataURL(artistPhoto);
  } else if (artPhoto) {
    let artReader = new FileReader();

    artReader.onload = function(event) {
      artImage = event.target.result;
      createStoryCard(name, title, story, artistImage, artImage);
    };

    artReader.readAsDataURL(artPhoto);
  } else {
    createStoryCard(name, title, story, artistImage, artImage);
  }
}

function createStoryCard(name, title, story, artistImage, artImage) {
  let storySection = document.getElementById("stories");

  let newPost = document.createElement("div");
  newPost.className = "story-card";

  newPost.innerHTML = `
    <div class="artist-info">
      ${
        artistImage
          ? `<img src="${artistImage}" class="artist-photo" alt="Artist photo">`
          : `<img src="https://via.placeholder.com/150" class="artist-photo" alt="Artist placeholder">`
      }

      <div>
        <h3>${title}</h3>
        <small>Posted by ${name}</small>
      </div>
    </div>

    ${
      artImage
        ? `<img src="${artImage}" class="art-photo" alt="Artwork photo">`
        : ""
    }

    <p>${story}</p>

    <button class="like-btn" onclick="likeStory(this)">
      ❤️ Like <span>0</span>
    </button>

    <div class="reply-box">
      <input type="text" placeholder="Your name" class="reply-name">
      <textarea placeholder="Write a response..." class="reply-text"></textarea>
      <button onclick="addReply(this)">Reply</button>
    </div>

    <div class="replies"></div>
  `;

  storySection.prepend(newPost);

  document.getElementById("name").value = "";
  document.getElementById("title").value = "";
  document.getElementById("story").value = "";
  document.getElementById("artistPhoto").value = "";
  document.getElementById("artPhoto").value = "";
}

function likeStory(button) {
  let likeCount = button.querySelector("span");
  let count = Number(likeCount.textContent);
  count++;
  likeCount.textContent = count;
}

function addReply(button) {
  let storyCard = button.closest(".story-card");
  let replyName = storyCard.querySelector(".reply-name").value;
  let replyText = storyCard.querySelector(".reply-text").value;
  let replies = storyCard.querySelector(".replies");

  if (replyName === "" || replyText === "") {
    alert("Please enter your name and response.");
    return;
  }

  let newReply = document.createElement("div");
  newReply.className = "reply";

  newReply.innerHTML = `
    <strong>${replyName}</strong>
    <p>${replyText}</p>
  `;

  replies.appendChild(newReply);

  storyCard.querySelector(".reply-name").value = "";
  storyCard.querySelector(".reply-text").value = "";
}
</script>

</body>
</html>
