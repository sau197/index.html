import os
import time

PROMPT_FILE = "prompts.txt"
OUTPUT_FOLDER = "output"

def load_prompts():
    with open(PROMPT_FILE, "r", encoding="utf-8") as f:
        prompts = f.readlines()
    return [p.strip() for p in prompts]

def generate_ai_image(prompt, index):
    print(f"Generating AI image {index}...")
    filename = f"{OUTPUT_FOLDER}/image_{index}.png"

    # giả lập tạo ảnh
    with open(filename, "w") as f:
        f.write(prompt)

    time.sleep(1)
    return filename

def create_video(images):
    print("Creating video from images...")

    video_file = f"{OUTPUT_FOLDER}/video.mp4"

    with open(video_file, "w") as f:
        f.write("AI video generated")

    return video_file

def main():

    if not os.path.exists(OUTPUT_FOLDER):
        os.makedirs(OUTPUT_FOLDER)

    prompts = load_prompts()

    images = []

    for i, prompt in enumerate(prompts):
        img = generate_ai_image(prompt, i)
        images.append(img)

    video = create_video(images)

    print("Video created:", video)

if __name__ == "__main__":
    main()
