<%*
const clip = await navigator.clipboard.read();
if(clip[0] && clip[0].types.includes('text/html')) {
	const htmlBlob = await clip[0].getType('text/html');
	const html  = await (new Response(htmlBlob)).text();
	//tR += "```\n"+html+"\n```\n\n"
	const parser = new DOMParser();
	const doc =  parser.parseFromString(html, "text/html"); 
	const messages = Array.from(doc.querySelectorAll('.c-message_kit__message'));
	messages.forEach((m) => {
		const sender = m.querySelector('.c-message__sender_button');
		if(sender) {
			tR += `[[${sender.innerText}]]\n`;
		}
		const body = m.querySelector('.c-message_kit__blocks');
		if(body) {
			tR += `${tp.obsidian.htmlToMarkdown(body.innerHTML)}\n`;
		}
		const text = m.querySelector('.c-message_kit__text');
		if(text) {
			tR += `${text.innerText}\n`;
		}
		tR += '\n'
	});
} else {
	tR = 'no html in clipboard';
}
%>