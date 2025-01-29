<%*

/*
# How to use
Create a new document, and give it the name of the YouTube Video ID. So in
https://www.youtube.com/watch?v=TTMiILxqBSc
that would be:
TTMiILxqBSc
Then apply this template using Templater.
The Template will:
- Get the details of the video,
- Rename the document to the video's title,
- Add a link to the Author of the video, and
- Embed a player so that you can watch the video.
*/

async function apiGet(url, data) {
  let finalURL = new URL(url);
  if (data)
    Object.keys(data).forEach((key) =>
      finalURL.searchParams.append(key, data[key])
    );

  const res = await request({
    url: finalURL.href,
    method: "GET",
    cache: "no-cache",
    headers: {
      "Content-Type": "application/json",
    },
  });

  return JSON.parse(res);
}

async function getYoutubeDetails(tp){
  const youtubeId = tp.file.title;
  const youtubeUrl = 'https://www.youtube.com/oembed?url=http://www.youtube.com/watch?v=' +  youtubeId + '&format=json';
  var yt = await apiGet(youtubeUrl, {});
  yt['youtubeId'] = youtubeId;
  return yt;
}

const youtube = await getYoutubeDetails(tp);

const filename = youtube.title
    .replace(/:/gi, ' -')
    .replace(/\|/gi, '-')
    .replace(/\$/gi, '-')
    .replace(/\//gi, '-')
    .replace(/\?/gi, '')
    .replace(/\*/gi, '')
;
console.log(filename);
await tp.file.move(`Videos/${filename}`);

-%>
# <% youtube.title %>

created:: <% tp.date.now("YYYY-MM-DDTHH:mm") %>
author:: Guillaume Hanique

#video

Links:

- is:: [[YouTube Video]]
- author:: [[<% youtube.author_name %>]]

<iframe width="560" height="315" src="https://www.youtube.com/embed/<% youtube.youtubeId %>" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## References

- source:: https://www.youtube.com/watch?v=<% youtube.youtubeId %>
