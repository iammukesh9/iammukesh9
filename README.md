public class InstagramLogin {
    public static void main(String[] args) {
        String clientId = "YOUR_INSTAGRAM_CLIENT_ID";
        String redirectUri = "YOUR_REDIRECT_URI";
        String authUrl = "https://api.instagram.com/oauth/authorize"
                + "?client_id=" + clientId
                + "&redirect_uri=" + redirectUri
                + "&scope=user_profile,user_media"
                + "&response_type=code";

        System.out.println("Open the following URL in your browser to login:");
        System.out.println(authUrl);
    }
}
import java.io.*;
import java.net.*;
import java.nio.charset.StandardCharsets;

public class InstagramTokenExchange {
    public static void main(String[] args) throws IOException {
        String code = "CODE_FROM_REDIRECT";
        String clientId = "YOUR_CLIENT_ID";
        String clientSecret = "YOUR_CLIENT_SECRET";
        String redirectUri = "YOUR_REDIRECT_URI";

        URL url = new URL("https://api.instagram.com/oauth/access_token");
        HttpURLConnection conn = (HttpURLConnection) url.openConnection();
        conn.setRequestMethod("POST");
        conn.setDoOutput(true);

        String params = "client_id=" + clientId +
                "&client_secret=" + clientSecret +
                "&grant_type=authorization_code" +
                "&redirect_uri=" + redirectUri +
                "&code=" + code;

        try (OutputStream os = conn.getOutputStream()) {
            os.write(params.getBytes(StandardCharsets.UTF_8));
        }

        BufferedReader br = new BufferedReader(new InputStreamReader(conn.getInputStream()));
        String responseLine;
        StringBuilder response = new StringBuilder();
        while ((responseLine = br.readLine()) != null) {
            response.append(responseLine);
        }

        System.out.println("Access token response: " + response);
    }
}


- 👋 Hi, I’m @iammukesh9
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
iammukesh9/iammukesh9 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
