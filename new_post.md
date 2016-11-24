---
layout: page
permalink: /new_post/
---

# Create a New Post

Here you can generate a post template at GitHub for a new blog post.

<form>
Post Title<br>
<input type="text" id="post_title">
<br>
<br>
<!-- Add lists with categories and tags here ?? -->
<button type="submit" id="create_button">Propose Post</button>
</form>

<script type="text/javascript">
  function create_new_post()
  {
    var title = document.getElementById("post_title").value;

    if (title != "")
    {
      var title_raw = title;
      title = title.replace(/ /g, "-").replace(/\//g, "");
      var date = new Date();
      var url = "https://github.com/{{site.github_username}}{{site.baseurl}}/new/master?filename=_posts/"
        + date.getFullYear() + "-" + (date.getMonth() + 1) + "-" + date.getDate() + "-" + title + ".md";

      var default_text = [
        '---',
        'layout: post',
        'title: "' + title_raw + '"',
        'description: "Short summary displayed at the main page"',
        'discussion: true',
        'category: foo',
        'tags: [ tag1, tag2 ]',
        '---',
        '',
        'Your new post here.'
      ].join('\n');

      url += "&value=" + encodeURIComponent(default_text);
      window.open(url);
    }
  }

  window.onload = function() {
    document.getElementById("create_button").onclick = create_new_post;
  };

</script>
