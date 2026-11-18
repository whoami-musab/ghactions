const dotenv = require("dotenv");
dotenv.config();

const repository_dispatch = async () => {
  try {
    const res = await fetch(
      "https://api.github.com/repos/whoami-musab/ghactions/dispatches",
      {
        method: "POST",
        headers: {
          Authorization: `Bearer ${process.env.ghaction_token}`,
          Accept: "application/vnd.github+json",
          "Content-Type": "application/json",
          "X-Github-Api-Version": "2022-11-28",
        },
        body: JSON.stringify({ event_type: "incident_report" }),
      },
    );
    if (!res.ok) {
      const error = await res.json();
      throw new Error(`Github Api Err ${res.status}: ${JSON.stringify(error)}`);
    }
    console.log({ success: true });
    return {
      success: true,
      status: res.status,
    };
  } catch (error) {
    console.error("Repository Dispatch Error: ", error.message);
    return {
      success: false,
      error: error.message,
    };
  }
};

repository_dispatch().then((result) => {
  console.log("Dispatch result: ", result);
});
