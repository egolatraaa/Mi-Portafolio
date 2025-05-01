<script setup>
import { h, ref } from "vue";
import {
  EnvelopeIcon,
  CodeBracketIcon,
  UserIcon,
  ComputerDesktopIcon,
  ServerStackIcon,
  CircleStackIcon,
  BriefcaseIcon,
} from "@heroicons/vue/24/outline";
import { Github, Mail, Terminal, School } from "lucide-vue-next";
import { onMounted } from "vue";

const showModal = ref(false);
const showEssenzia = ref(false);

// Definimos los componentes SVG directamente
const FlaskIcon = {
  render() {
    return h(
      "svg",
      {
        xmlns: "http://www.w3.org/2000/svg",
        width: "512",
        height: "512",
        viewBox: "0 0 512 512",
        class: "w-5 h-5",
      },
      [
        h("path", {
          fill: "currentColor",
          d: "M153.001 434.531c-53.682-31.457-99.53-107.4-123.226-174.012c-9.518-28.896-12.778-59.876-25.048-87.656c-12.835-20.176 2.2-42.233 24.3-48.646c9.84-1.889 27.142-11.17 6.257-4.536c-18.723 13.737-20.535-12.47-1.336-14.13c13.103-1.74 17.927-12.467 13.446-22.123c-14.065-9.172 34.106-19.253 9.868-32.939c-25.25-27.24 35.318-32.485 20.375-1.547c-3.577 23.79 42.322-4.36 31.673 23.111c10.824 13.193 40.533 3.003 39.796 21.512c15.768 1.084 21.18 14.35 35.982 15.37c15.34 6.927 43.151 12.386 48.371 29.674c-15.22 12.05-50.463-24.89-52.156 8.464c6.422 117.654 12.507 158.22 69.32 219.855c38.268 43.3 90.852 63.719 135.244 70.988c9.562-7.314 26.444-34.505 41.36-23.04c.709 12.884-29.606 26.932-1.425 25.509c16.547-4.992 28.025 12.797 41.651-3.25c12.555 14.872 52.18-9.5 43.248 20.896c-12.078 7.792-29.695 3.083-41.793 13.804c-19.948-9.963-35.83 8.915-57.913 6.527c-85.133 14.9-196.073 1.46-257.994-43.831m100.061 36.821c37.114 5.162 75.442 13.102 112.689 5.86c-16.858-7.613-34.286 2.965-51.08-5.444c-20.142 4.335-41.757-1.104-62.234-3.781c-23.286-10.373-48.416-17.505-70.222-30.968c-27.248-9.953 14.092 12.763 21.45 14.603c17.034 9.668-18.73-4.957-23.773-8.976c-14.266-8.003-16.445-6.137-1.773 1.99c22.878 14.173 51.55 23.782 74.943 26.716m-106.228-50.599c20.684 7.662-.092-14.546-9.57-13.255c-4.2-7.286-16.044-11.888-7.689-15.802c-15.03 5.218-15.744-19.842-22.81-16.262c-15.9-5.02-6.188-22.806-25.128-33.729c-1.729-11.508-18.818-21.49-24.268-38.85c-2.408-8.888-19.307-34.412-8.926-10.658c8.84 22.866 24.392 42.449 37.334 62.01c10.05 18.623 21.916 38.087 40.218 49.705c6.17 5.918 12.126 14.986 20.839 16.841m26.638-36.043c-11.317-6.033-35.955-9.155-18.569 4.646c11.161 4.51 39.606 6.698 18.57-4.646m18.97 23.984c24.306 6.876-20.44-15.371-5.998-2.53zm.205-12.88c17.658 2.277-21.01-12.01-3.874-1.278zm61.37 37.735c16.486-9.856 11.051 23.08 27.97 2.782c16.688-12.185-14.412 15.065 6.156 2.173c14.874-9.949 36.845 4.716 50.724 9.5c9.982-.49 19.685 8.632 29.917 3.083c19.698-5.306-38.518-7.87-23.257-17.282c-18.024 5.245-31.34-6.254-40.209-17.798c-20.217-4.669-43.592-15.005-53.682-32.896c-4.114-6.718 5.943.946-3.55-10.034c-12.183-10.836-18.266-23.136-26.444-36.307c-9.77-5.212-10.908-20.552-11.896-.514c.078-12.646-11.795-21.158-14.693-17.62c-.052-12.18 12.706-6.074 3.775-15.086c-1.922-12.623-8.252-25.777-10.154-40.029c-2.956-6.87-.416-21.584-10.089-6.032c-3.524 16.437-1.17-20.198 4.31-8.118c7.193-12.327-2.582-10.877-2.982-9.165c4.685-10.402 2.966-25.155-1.223-19.527c2.497-11.023 3.945-40.57-3.736-35.335c4.656-11.527 8.83-52.748-11.382-37.032c-8.192.115-22.377 2.974-29.082 6.308c21.024 11.59-2.115 4.186-10.673 2.344c-1.116 10.723-9.592 6.085-20.182 6.19c16.914 2.093-8.237 17.3-17.94 11.393c-12.603 6.023 10.875 21.058.252 25.706c1.306 7.008-19.306-2.53-17.688 13.654c-12.234-5.147-1.684 19.198 4.437 10.965c20.808 5.631 14.648 18.47 15.178 30.667c-3.39 7.107-16.739-16.705-2.973-15.602c-10.86-17.642-12.013-6.377-21.038 1.819c-2.099.595 23.02 11.66 7.256 17.133c13.869 2.14 14.263 14.276 17.087 21.956c8.335 8.682 6.63-9.587 16.603.846c-6.311-9.295-33.431-26.19-11.596-20.771c-.117-9.356-3.95-16.9 2.74-16.717c6.625-11.997-6.938 29.58 7.995 14.333c4.133-1.805 5.157-12.012 12.587.964c10.792 10.616 3.898 18.309-11.325 8.588c2.724 9.24 20.364 12.541 17.05 26.99c3.514 12.706 8.43 8.026 12.716 7.291c3.362 12.347 5.271 3.268 5.43-2.607c15.395 3.295 11.789 12.395 16.606 18.752c10.607 4.788-15.183-32.454 3.028-11.198c19.16 17.298 7.29 23.261-10.009 21.748c14.388 1.178 14.69 13.994 28.005 14.165c11.572 5.967 20.693 28.354-.704 18.913c-12.065-7.486-33.558-14.714-12.108-1.987c5.077 3.214 35.545 14.663 54.652 26.178c10.579 7.232 19.582 20.943 24.765 23.156c-11.493 5.49-34.634-4.383-17.45-7.409c-10.719-1.952-22.402-7.45-12.508 5.982c8.508 7.779 30.928 6.517 34.907 7.342c-3.373 7.433-9.162 8.024.139 8.6c-10.376 5.53 3.327 6.386 4.288 9.545m-22.337-68.123c-6.824-10.76-5.192 1.606 1.12 8.207c10.09 12 2.379-6.802-1.12-8.207m-37.672-55.658s1.682-11.35-3.507-12.605c-5.19-1.256-2.33.834 1.822 9.819c.99 2.143 1.602 2.886 1.594 2.837m-56.712-43.072c-5.155-11.545 2.453-5.276 1.345-10.2c-2.38-4.95-25.508-31.236-14.973-11.391c9.534 23.673-5.998-2.972-7.618-11.038c-1.791 4.953 3.772 21.176 7.135 26.705c8.561 13.185 4.71-7.22 14.11 5.924m-47.363-45.524c-13.386-11.26 4.127 5.55-1.309 5.338c-14.107-10.303-8.34-3.004-.372 4.914c8.632 12.827 15.757-7.686 1.681-10.252m6.873 1.936c25.322 6.957-26.949-24.436-3.785-3.822zm70.076 29.93c-7.268.147 3.014-15.827-6.73-12.675c-3.419-24.828-10.786 11.474-.762 17.484c3.095 8.893 6.346 5.27 7.492-4.81m-59.785-35.319c33.717 15.562-24.413-25.739-9.532-5.207c1.769 3.957 6.008 4.286 9.532 5.207m3.864-8.066c25.537 10.556-2.272-6.869-11.116-4.977c2.23 3.263 8.278 1.836 11.116 4.977m3.42-9.555c8.29-1.656-1.1-4.314-6.054-8.25c-11.465-17.223 1.705 1.39-1.898 6.677c4.771 4.69 20.99 13.075 7.951 1.573m58.647-26.721c-3.385 17.891-6.838 10.43-1.985-2.91c-1.161-17.12-11.565 10.484-6.967 18.587c7.602 12.109 15.204-29.758 8.952-15.677m10.109 213.016c13.167 3.379 13.1-2.048 1.2-3.66c-6.402-5.955-26.599-12.271-8.521-.74c1.197 3.033 4.98 2.963 7.32 4.4m-46.75-31.05c7.254 5.409 27.323 15.33 10.334 2.058c5.728-6.654-10.963-10.197-5.426-14.648c-14.084-8.618-11.11-7.852-1.244-7.58c-16.925-7.566 2.444-7 1.532-10.877c-6.527-1.289-32.417-11.508-17.186.84c-15.484-7.895-3.69 2.94-8.37 1.795c-15.833-4.317 14.1 12.059-2.514 7.994c9.083 7.198 24.449 18.438 3.84 7.617c-2.716 3.909 14.748 9.834 19.034 12.8m164.515 96.479c6.945-6.73.284 10.72 11.508-1.648c.121-8.853-.346-14.082-12.898-3.328c-3.46 1.92-5.005 10.079 1.39 4.976m-113.73-73.02c7.725 6.863 35.482 5.036 9.383.845c-3.866-5.715-24.545-4.34-9.383-.844M59.833 293.379c-11.223-16.012-6.976-23.21-17.799-36.283c-2.048-9.998-18.565-32.685-8.543-8.65c9.18 14.057 11.909 35.822 26.342 44.933M392.335 451.41c10.919-2.213 35.8 5.558 39.821-2.895c-13.259-.321-45.873-9.354-47.417 2.156zm-371.8-275.906c-1.99-11.407-4.396-31.43 14.638-24.664c-25.407 5.044 17.584 31.579 12.155 10.629c10.683.523 20.899-6.314 15.293 4.062c21.048-2.325 35.641-20.578 55.973-18.02c15.838-2.096 33.154-3.685 50.22-10.06c14.033-1.011 27.541-16.12 19.85-25.074c-19.136-1.619-39.168.775-60.318 4.98c-23.438 4.872-44.727 14.129-68.375 18.102c-23.05 3.096 4.637 8.531-1.966 9.742c-12.028 4.173 14.344 6.988-1.56 11.387c-9.82-1.867-20.044-5.242-15.849-15.592c-22.08 2.865-41.481 12.029-24.037 34.498zm59.011-24.563c19.25 13.16-3.308-21.605-8.485-2.533c2.405-.592 6.186.812 8.485 2.533m5.48-8.819c18.248 1.836-2.796-11.586-3.47-3.159zm30.583-11.176c26.935-5.127-9.864-8.558-17.755.925c5 2.28 10.535-6.36 17.755-.925m46.2-9.176c17.028-2.615 2.677-10.431-2.305 2.623c1.806 4.116 2.675-1.234 2.305-2.623m-91.595 69.56c9.624-.66 15.057-10.616-1.862-10.044c-26.221-2.714 23.135 8.979-3.363 5.635c-3.561 2.358 5.018 5.062 5.225 4.41M56.737 115.31c17.176-5.843 38.86-10.806 48.527 3.286c-7.272-10.259-3.083-20.122 4.712-5.598c11.024 14.696 14.979-3.775 9.372-11.613c5.335 8.437 25.138 26.808 5.47.642c13.033-15.677-26.094 2.053-34.987 1.874c-4.28 1.92-44.177 10.175-33.094 11.41m10.066-19.278c9.796-7.394 33.88 4.398 18.425-7.348c-1.51-1.335-33.844 8.907-18.425 7.348m35.713 1.474c11.464.293-4.946-15.401 8.716-8.29c-2.244-7.33-15.906-8.702-22.585-11.63c-3.778 6.701 7.69 20.01 13.869 19.92m-42.109-50.25C47.4 30.274 84.872 50.11 71.655 32.33c-11.124-8.858-21.813 9.969-11.248 14.926m166.945 89.921c5.967-10.576-24.633-14.257-4.02-3.748c1.898.634 1.469 4.48 4.02 3.748",
        }),
      ]
    );
  },
};

const PythonIcon = {
  render() {
    return h(
      "svg",
      {
        xmlns: "http://www.w3.org/2000/svg",
        width: "24",
        height: "24",
        viewBox: "0 0 24 24",
        class: "w-5 h-5 text-[#3776AB]",
      },
      [
        h("g", { fill: "none" }, [
          h(
            "g",
            { fill: "currentColor", "clip-path": "url(#akarIconsPythonFill0)" },
            [
              h("path", {
                d: "M11.914 0C5.82 0 6.2 2.656 6.2 2.656l.007 2.752h5.814v.826H3.9S0 5.789 0 11.969s3.403 5.96 3.403 5.96h2.03v-2.867s-.109-3.42 3.35-3.42h5.766s3.24.052 3.24-3.148V3.202S18.28 0 11.913 0M8.708 1.85c.578 0 1.046.47 1.046 1.052c0 .581-.468 1.051-1.046 1.051s-1.046-.47-1.046-1.051c0-.582.467-1.052 1.046-1.052",
              }),
              h("path", {
                d: "M12.087 24c6.092 0 5.712-2.656 5.712-2.656l-.007-2.752h-5.814v-.826h8.123s3.9.445 3.9-5.735s-3.404-5.96-3.404-5.96h-2.03v2.867s.109 3.42-3.35 3.42H9.452s-3.24-.052-3.24 3.148v5.292S5.72 24 12.087 24m3.206-1.85c-.579 0-1.046-.47-1.046-1.052c0-.581.467-1.051 1.046-1.051c.578 0 1.046.47 1.046 1.051c0 .582-.468 1.052-1.046 1.052",
              }),
            ]
          ),
          h("defs", [
            h("clipPath", { id: "akarIconsPythonFill0" }, [
              h("path", { fill: "#fff", d: "M0 0h24v24H0z" }),
            ]),
          ]),
        ]),
      ]
    );
  },
};

const VueIcon = {
  render() {
    return h(
      "svg",
      {
        xmlns: "http://www.w3.org/2000/svg",
        width: "15",
        height: "15",
        viewBox: "0 0 15 15",
        class: "w-5 h-5 text-[#4FC08D]",
      },
      [
        h("path", {
          fill: "currentColor",
          d: "M2.717 1H.5a.5.5 0 0 0-.432.752l7 12a.5.5 0 0 0 .864 0l7-12A.5.5 0 0 0 14.5 1h-2.217L7.5 8.972z",
        }),
        h("path", {
          fill: "currentColor",
          d: "M11.117 1H8.19L7.5 2.382L6.809 1H3.883L7.5 7.028z",
        }),
      ]
    );
  },
};

const TailwindIcon = {
  render() {
    return h(
      "svg",
      {
        xmlns: "http://www.w3.org/2000/svg",
        width: "24",
        height: "24",
        viewBox: "0 0 24 24",
        class: "w-5 h-5 text-[#06B6D4]",
      },
      [
        h("path", {
          fill: "currentColor",
          d: "M12 6c-2.67 0-4.33 1.33-5 4c1-1.33 2.17-1.83 3.5-1.5c.76.19 1.31.74 1.91 1.35c.98 1 2.09 2.15 4.59 2.15c2.67 0 4.33-1.33 5-4c-1 1.33-2.17 1.83-3.5 1.5c-.76-.19-1.3-.74-1.91-1.35C15.61 7.15 14.5 6 12 6m-5 6c-2.67 0-4.33 1.33-5 4c1-1.33 2.17-1.83 3.5-1.5c.76.19 1.3.74 1.91 1.35C8.39 16.85 9.5 18 12 18c2.67 0 4.33-1.33 5-4c-1 1.33-2.17 1.83-3.5 1.5c-.76-.19-1.3-.74-1.91-1.35C10.61 13.15 9.5 12 7 12",
        }),
      ]
    );
  },
};

const MongoIcon = {
  render() {
    return h(
      "svg",
      {
        xmlns: "http://www.w3.org/2000/svg",
        width: "24",
        height: "24",
        viewBox: "0 0 24 24",
        class: "w-5 h-5 text-[#47A248]",
      },
      [
        h("path", {
          fill: "currentColor",
          d: "M13.74 4.23a35 35 0 0 1-1.713-2.216a.033.033 0 0 0-.054 0a35 35 0 0 1-1.713 2.217c-7.212 9.187 1.138 15.385 1.138 15.385l.067.047c.064.959.221 2.337.221 2.337h.628s.157-1.372.22-2.33l.069-.054s8.349-6.198 1.138-15.385M12 19.482s-.374-.32-.475-.48l-.001-.016l.453-10.002a.024.024 0 0 1 .047 0l.452 10.002v.017c-.101.16-.476.48-.476.48",
        }),
      ]
    );
  },
};

const FirebaseIcon = {
  render() {
    return h(
      "svg",
      {
        xmlns: "http://www.w3.org/2000/svg",
        width: "24",
        height: "24",
        viewBox: "0 0 24 24",
        class: "w-5 h-5 text-[#FFCA28]",
      },
      [
        h("path", {
          fill: "currentColor",
          d: "m20 18.69l-7.3 4.05q-.75.39-1.5 0L4 18.69L17.05 5.54l.35-.1c.3 0 .47.13.5.4zM9.35 5.74L4.8 13.29L6.7 1.34c.03-.27.2-.4.5-.4c.2 0 .33.06.4.25l2.15 3.95zM13.85 7L4.3 16.59l7.25-12.3c.1-.2.25-.29.45-.29s.33.09.4.29z",
        }),
      ]
    );
  },
};

onMounted(() => {
  const animateOnScroll = () => {
    const elements = document.querySelectorAll('[class*="animate-"]');
    const windowHeight = window.innerHeight;
    const triggerOffset = 100;

    elements.forEach((element) => {
      const elementTop = element.getBoundingClientRect().top;

      if (elementTop < windowHeight - triggerOffset) {
        const animationClass = Array.from(element.classList).find((cls) =>
          cls.startsWith("animate-")
        );

        if (animationClass && !element.classList.contains("animated")) {
          element.classList.add("animated"); // Marca como animado
          element.style.opacity = "1"; // Asegúrate de que sea visible
        }
      }
    });
  };

  // Ejecutar al cargar y al hacer scroll
  window.addEventListener("scroll", animateOnScroll);
  animateOnScroll();
});
</script>

<template>
  <main
    className="min-h-screen bg-gradient-to-b from-blue-900 via-zinc-950 via-25% to-zinc-950 text-gray-100 font-['Inter']"
  >
    <div class="mx-auto max-w-5xl w-full px-4 sm:px-6 lg:px-8">
      <!-- Hero / Intro -->
      <section
        class="flex flex-col md:flex-row justify-center items-center h-screen px-4 md:px-20 gap-8 md:gap-12"
      >
        <div class="flex flex-col md:flex-row items-center gap-6 md:gap-8">
          <div class="order-2 md:order-1 max-w-md">
            <div
              class="inline-flex items-center gap-2 bg-zinc-700 text-indigo-300 px-4 py-1 rounded-full mb-4"
            >
              <Terminal class="w-5 h-5" />
              <span class="text-sm font-medium">Desarrollador Web</span>
            </div>
            <h1
              class="text-4xl md:text-5xl font-bold mb-4 text-white font-['Poppins']"
            >
              Hola, soy Abdiel
            </h1>
            <p class="text-xl md:text-2xl text-gray-300 mb-6">
              Ingeniero en desarrollo de software
            </p>

            <!-- Contenedor de botones centrados -->
            <div
              class="flex flex-col md:flex-row gap-4 items-center justify-center text-center"
            >
              <a
                href="#proyectos"
                class="flex items-center justify-center gap-2 bg-indigo-600 text-white px-6 py-3 rounded-xl hover:bg-indigo-700 transition font-medium"
              >
                <CodeBracketIcon class="w-5 h-5" />
                Ver proyectos
              </a>
              <a
                href="https://github.com/egolatraaa"
                target="_blank"
                class="flex items-center justify-center gap-2 border border-zinc-600 text-gray-300 px-6 py-3 rounded-xl hover:bg-zinc-700 transition font-medium"
              >
                <Github class="w-5 h-5" />
                GitHub
              </a>
            </div>
          </div>

          <!-- Foto -->
          <div class="order-1 md:order-2 w-32 h-32 md:w-40 md:h-40">
            <img
              src="/yo.png"
              alt="Abdiel"
              class="w-full h-full object-cover rounded-full"
            />
          </div>
        </div>
      </section>

      <!-- Experiencia -->
      <section id="experiencia" class="py-20 px-6 md:px-20">
        <div class="max-w-4xl mx-auto">
          <h2
            class="text-3xl font-bold text-indigo-400 mb-12 font-['Poppins'] animate-fade-in-up opacity-0 animation-delay-100"
          >
            Experiencia
          </h2>

          <div class="relative">
            <div class="space-y-16 pl-16 md:pl-20">
              <!-- Freelance -->
              <div
                class="relative animate-fade-in-up opacity-0 animation-delay-300"
              >
                <!-- Icono de bolsa de trabajo -->
                <div
                  class="absolute -left-11 md:-left-12 top-1 w-8 h-8 md:w-10 md:h-10 rounded-full bg-indigo-500 flex items-center justify-center border-2 border-indigo-400/50 z-10"
                >
                  <svg
                    xmlns="http://www.w3.org/2000/svg"
                    class="h-5 w-5 text-white"
                    viewBox="0 0 20 20"
                    fill="currentColor"
                  >
                    <path
                      fill-rule="evenodd"
                      d="M6 6V5a3 3 0 013-3h2a3 3 0 013 3v1h2a2 2 0 012 2v3.57A22.952 22.952 0 0110 13a22.95 22.95 0 01-8-1.43V8a2 2 0 012-2h2zm2-1a1 1 0 011-1h2a1 1 0 011 1v1H8V5zm1 5a1 1 0 011-1h.01a1 1 0 110 2H10a1 1 0 01-1-1z"
                      clip-rule="evenodd"
                    />
                    <path
                      d="M2 13.692V16a2 2 0 002 2h12a2 2 0 002-2v-2.308A24.974 24.974 0 0110 15c-2.796 0-5.487-.46-8-1.308z"
                    />
                  </svg>
                </div>

                <!-- Tarjeta -->
                <div>
                  <p class="text-lg font-semibold text-white">
                    Desarrollador Web Freelance - Proyectos personales
                  </p>
                  <p class="text-sm text-indigo-400 mb-2">2023 - 2024</p>
                  <p class="text-gray-300 text-sm">
                    Desarrollé diversos sitios web y aplicaciones para
                    emprendimientos locales. Estos proyectos representaron una
                    etapa clave de aprendizaje práctico, fortaleciendo mis
                    habilidades en diseño responsivo e integración de bases de
                    datos.
                  </p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- Proyectos -->
      <section id="proyectos" class="py-20 px-6 md:px-20">
        <div class="max-w-6xl mx-auto">
          <h2 class="text-3xl font-bold text-indigo-400 mb-12 font-['Poppins']">
            Proyectos Recientes
          </h2>

          <div class="grid md:grid-cols-2 gap-10">
            <!-- Proyecto Essenzia -->
            <div
              class="bg-zinc-800 rounded-xl overflow-hidden flex flex-col border border-zinc-700 hover:border-indigo-500 transition"
            >
              <img
                src="/essenzia-proyecto.png"
                alt="Essenzia Preview"
                class="w-full h-48 object-cover"
              />
              <div class="flex flex-col flex-1 p-4">
                <!-- Flex-1 para que esta div se expanda -->
                <div>
                  <h3 class="text-2xl font-semibold mb-3 text-white">
                    Ecommerce Essenzia Shop
                  </h3>
                  <p class="text-gray-400 mb-4 text-sm">
                    Tienda online de perfumes premium con filtros inteligentes,
                    login OAuth y pagos seguros con Stripe.
                  </p>
                  <div class="flex flex-wrap gap-2 mb-4">
                    <span
                      class="px-3 py-1 bg-zinc-700 text-indigo-300 rounded-full text-xs flex items-center gap-1"
                    >
                      <VueIcon /> Vue
                    </span>
                    <span
                      class="px-3 py-1 bg-zinc-700 text-indigo-300 rounded-full text-xs flex items-center gap-1"
                    >
                      <TailwindIcon /> Tailwind
                    </span>
                    <span
                      class="px-3 py-1 bg-zinc-700 text-indigo-300 rounded-full text-xs flex items-center gap-1"
                    >
                      <FlaskIcon /> Flask
                    </span>
                    <span
                      class="px-3 py-1 bg-zinc-700 text-indigo-300 rounded-full text-xs flex items-center gap-1"
                    >
                      <MongoIcon /> MongoDB
                    </span>
                  </div>
                </div>

                <!-- Ahora sí: este link se manda hasta abajo -->
                <div class="mt-auto">
                  <a
                    href="https://frontend-essenzia-uf0t.onrender.com"
                    target="_blank"
                    class="text-indigo-400 text-sm hover:underline transition"
                  >
                    Ver proyecto
                  </a>
                </div>
              </div>
            </div>

            <!-- Proyecto La Perla Dorada -->
            <div
              class="bg-zinc-800 rounded-xl overflow-hidden flex flex-col border border-zinc-700 hover:border-indigo-500 transition"
            >
              <img
                src="/perladorada-proyecto.png"
                alt="La Perla Dorada Preview"
                class="w-full h-48 object-cover"
              />
              <div class="flex flex-col flex-1 p-4">
                <div>
                  <h3 class="text-2xl font-semibold mb-3 text-white">
                    Página Web La Perla Dorada
                  </h3>
                  <p class="text-gray-400 mb-4 text-sm">
                    Página web de presentación para un restaurante.
                  </p>
                  <div class="flex flex-wrap gap-2 mb-4">
                    <span
                      class="px-3 py-1 bg-zinc-700 text-indigo-300 rounded-full text-xs flex items-center gap-1"
                    >
                      <VueIcon /> Vue
                    </span>
                    <span
                      class="px-3 py-1 bg-zinc-700 text-indigo-300 rounded-full text-xs flex items-center gap-1"
                    >
                      <TailwindIcon /> Tailwind
                    </span>
                  </div>
                </div>

                <div class="mt-auto">
                  <a
                    href="https://egolatraaa.github.io/La-Perla-Dorada/"
                    target="_blank"
                    class="text-indigo-400 text-sm hover:underline transition"
                  >
                    Ver proyecto
                  </a>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- Tecnologías -->
      <section class="py-20 px-6 md:px-20">
        <div class="max-w-6xl mx-auto">
          <!-- Título más grande y centrado -->
          <h2
            class="text-4xl font-bold text-indigo-400 mb-12 text-center font-['Inter', sans-serif]"
          >
            Tecnologías
          </h2>

          <div class="grid grid-cols-1 md:grid-cols-2 gap-12">
            <!-- Frontend -->
            <div
              class="bg-zinc-700/50 rounded-xl p-6 border border-zinc-600 hover:border-indigo-400 transition transform hover:scale-105 hover:shadow-2xl hover:shadow-indigo-500/50"
            >
              <div class="flex justify-center items-center mb-8">
                <h3
                  class="text-4xl font-semibold text-transparent bg-clip-text bg-gradient-to-b from-indigo-500 to-white"
                >
                  Frontend
                </h3>
              </div>
              <!-- Logos más grandes y centrados -->
              <div class="grid grid-cols-2 gap-4 justify-center mb-4">
                <div class="flex justify-center items-center flex-col">
                  <VueIcon class="w-16 h-16" />
                  <p class="text-white text-lg mt-2">Vue</p>
                </div>
                <div class="flex justify-center items-center flex-col">
                  <TailwindIcon class="w-16 h-16" />
                  <p class="text-white text-lg mt-2">Tailwind</p>
                </div>
              </div>
            </div>

            <!-- Backend -->
            <div
              class="bg-zinc-700/50 rounded-xl p-6 border border-zinc-600 hover:border-emerald-400 transition transform hover:scale-105 hover:shadow-2xl hover:shadow-emerald-500/50"
            >
              <div class="flex justify-center items-center mb-8">
                <h3
                  class="text-4xl font-semibold text-transparent bg-clip-text bg-gradient-to-b from-emerald-500 to-white"
                >
                  Backend
                </h3>
              </div>
              <!-- Logos más grandes y centrados -->
              <div class="grid grid-cols-2 gap-4 justify-center mb-4">
                <div class="flex justify-center items-center flex-col">
                  <PythonIcon class="w-16 h-16" />
                  <p class="text-white text-lg mt-2">Python</p>
                </div>
                <div class="flex justify-center items-center flex-col">
                  <FlaskIcon class="w-16 h-16" />
                  <p class="text-white text-lg mt-2">Flask</p>
                </div>
              </div>
            </div>

            <!-- Bases de Datos (tercera tarjeta ocupa toda la fila) -->
            <div
              class="bg-zinc-700/50 rounded-xl p-6 border border-zinc-600 hover:border-blue-400 transition transform hover:scale-105 hover:shadow-2xl hover:shadow-blue-500/50 md:col-span-2"
            >
              <div class="flex justify-center items-center mb-8">
                <h3
                  class="text-4xl font-semibold text-transparent bg-clip-text bg-gradient-to-b from-blue-500 to-white"
                >
                  Bases de Datos
                </h3>
              </div>
              <!-- Logos más grandes y centrados -->
              <div class="grid grid-cols-2 gap-4 justify-center mb-4">
                <div class="flex justify-center items-center flex-col">
                  <MongoIcon class="w-16 h-16" />
                  <p class="text-white text-lg mt-2">MongoDB</p>
                </div>
                <div class="flex justify-center items-center flex-col">
                  <FirebaseIcon class="w-16 h-16" />
                  <p class="text-white text-lg mt-2">Firebase</p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- Sobre mí -->
      <section id="sobre-mi" class="py-20 px-6 md:px-20">
        <div class="max-w-4xl mx-auto">
          <!-- Título a la izquierda -->
          <h2 class="text-3xl font-bold text-indigo-400 mb-8 font-['Poppins']">
            Sobre Mí
          </h2>

          <!-- Imagen circular centrada -->
          <div class="flex justify-center mb-6">
            <img
              src="/yo.png"
              alt="Foto de perfil"
              class="w-64 h-64 rounded-full object-cover"
            />
          </div>

          <!-- Texto justificado -->
          <div class="space-y-6 text-justify">
            <p class="text-lg text-gray-300">
              ¡Hola! 👋 Soy un
              <span class="text-indigo-500 font-semibold"
                >Ingeniero en Desarrollo de Software</span
              >
              con más de
              <span class="text-indigo-500 font-semibold"
                >3 años de experiencia</span
              >
              creando soluciones digitales que combinan innovación y
              funcionalidad. Mi objetivo es construir aplicaciones que no solo
              sean eficientes, sino que también brinden una
              <span class="text-indigo-500 font-semibold"
                >experiencia de usuario excepcional</span
              >.
            </p>
            <p class="text-lg text-gray-300">
              Cuando no estoy programando, me dedico a explorar nuevas
              tecnologías y compartir mis conocimientos con la comunidad.
              Siempre estoy en busca de oportunidades para seguir aprendiendo y
              creciendo.
            </p>
          </div>

          <!-- Botón centrado -->
          <div class="flex justify-center mt-10">
            <a
              href="/Mi-Portafolio/OscarIbarraranCV.pdf"
              dowload="OscarIbarraranCV.pdf"
              class="group relative inline-flex items-center gap-2 overflow-hidden bg-gray-700 text-white font-semibold py-3 px-6 rounded-xl transition-all duration-300"
            >
              <!-- Fondo animado -->
              <span
                class="absolute inset-0 bg-indigo-600 translate-x-[-100%] group-hover:translate-x-0 transition-transform duration-500 ease-in-out"
              ></span>

              <!-- Contenido encima -->
              <span class="relative flex items-center gap-2 z-10">
                <!-- Icono de hoja -->
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  class="h-5 w-5"
                  fill="none"
                  viewBox="0 0 24 24"
                  stroke="currentColor"
                >
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width="2"
                    d="M9 12h6m2 4H7m5-16h2a2 2 0 012 2v2m0 0h2a2 2 0 012 2v10a2 2 0 01-2 2H7a2 2 0 01-2-2V8a2 2 0 012-2h2V4a2 2 0 012-2z"
                  />
                </svg>
                Currículum
              </span>
            </a>
          </div>
        </div>
      </section>

      <!-- Contacto -->
      <section class="py-12 px-6 md:px-20 border-t border-zinc-700">
        <div class="max-w-4xl mx-auto text-center">
          <p class="text-gray-400 mb-2">¿Interesado en trabajar juntos?</p>
          <a
            href="mailto:ibarraranoscar@gmail.com"
            class="inline-flex items-center gap-2 text-indigo-400 hover:text-indigo-300 transition text-lg"
          >
            <Mail class="w-5 h-5" />
            ibarraranoscar@gmail.com
          </a>
          <div class="border-t border-zinc-700 mt-8 pt-8">
            <p class="text-gray-400 text-sm">
              © 2023 Abdiel - Todos los derechos reservados
            </p>
          </div>
        </div>
      </section>
    </div>
  </main>
</template>

<style>
@import url("https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&family=Poppins:wght@600;700&display=swap");

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.2s ease;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

[class*="animate-"] {
  opacity: 0; /* Ocultar inicialmente */
  transition: opacity 0.3s ease; /* Suavizar la transición */
}

/* Animaciones personalizadas */
@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

.animate-fade-in-up {
  animation: fadeInUp 0.6s ease-out forwards;
}

.animate-fade-in {
  animation: fadeIn 0.5s ease-out forwards;
}

.animation-delay-100 {
  animation-delay: 100ms;
}

.animation-delay-200 {
  animation-delay: 200ms;
}

.animation-delay-300 {
  animation-delay: 300ms;
}

.animation-delay-400 {
  animation-delay: 400ms;
}
</style>
