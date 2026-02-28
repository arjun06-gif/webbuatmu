import React, { useState, useMemo } from "react";
import { motion } from "framer-motion";
import { Heart, Sparkles } from "lucide-react";
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";

export default function RomanticWebsite() {
  const [step, setStep] = useState(0);
  const [loveLevel, setLoveLevel] = useState(0);
  const [showSecret, setShowSecret] = useState(false);
  const [showForeverPopup, setShowForeverPopup] = useState(false);
  const [showYesScene, setShowYesScene] = useState(false);
  const [noPosition, setNoPosition] = useState({ x: 0, y: 0 });

  const messages = [
    "Hai Mawar Sayang 😏",
    "Iya kamu, Mawar yang paling manis itu...",
    "Coba senyum dulu dong, Mawar...",
    "Nah gitu, Mawar cantik banget sih 💖",
  ];

  const petals = useMemo(() => {
    return Array.from({ length: 15 }).map((_, i) => ({
      id: i,
      left: Math.random() * 100,
      duration: 6 + Math.random() * 4,
      delay: Math.random() * 5,
      size: 20 + Math.random() * 20,
    }));
  }, []);

  const moveNoButton = () => {
    const rangeX = window.innerWidth < 500 ? 80 : 150;
    const rangeY = window.innerWidth < 500 ? 60 : 120;

    const randomX = Math.floor(Math.random() * rangeX - rangeX / 2);
    const randomY = Math.floor(Math.random() * rangeY - rangeY / 2);

    setNoPosition({ x: randomX, y: randomY });
  };

  return (
    <div className="relative min-h-screen bg-gradient-to-br from-purple-200 via-pink-200 to-rose-300 flex flex-col items-center justify-center p-6 text-center overflow-hidden">
      {/* Falling Petals */}
      {petals.map((petal) => (
        <motion.div
          key={petal.id}
          initial={{ y: -100, opacity: 0 }}
          animate={{ y: "110vh", opacity: [0, 1, 1, 0], rotate: 360 }}
          transition={{
            duration: petal.duration,
            repeat: Infinity,
            delay: petal.delay,
            ease: "linear",
          }}
          style={{
            position: "absolute",
            left: `${petal.left}%`,
            fontSize: petal.size,
          }}
        >
          🌸
        </motion.div>
      ))}

      {/* SUCCESS SCENE AFTER YES */}
      {showYesScene && (
        <motion.div
          initial={{ opacity: 0, scale: 0.9 }}
          animate={{ opacity: 1, scale: 1 }}
          className="fixed inset-0 bg-gradient-to-br from-rose-400 via-pink-400 to-purple-500 flex flex-col items-center justify-center text-white z-50 p-6 text-center space-y-6"
        >
          <h1 className="text-3xl md:text-5xl font-bold">
            YEAYYY 💖🌹
          </h1>

          <p className="text-lg md:text-2xl max-w-xl">
            Makasih udah pilih "Yes"...
            <br />
            Dari semua kemungkinan di dunia ini,
            <br />
            kamu tetap pilih aku.
          </p>

          <p className="text-xl md:text-3xl font-bold">
            Aku janji akan jaga Mawar selalu ❤️
          </p>

          {/* OPTIONAL PHOTO SECTION */}
          <div className="mt-4">
            <img
              src="/mawar-photo.jpg"
              alt="Jun dan Mawar"
              className="rounded-3xl shadow-2xl mx-auto w-64 h-64 object-cover"
              onError={(e) => {
                e.currentTarget.style.display = 'none';
              }}
            />
          </div>

          <Button
            className="mt-6 rounded-2xl px-6 py-4 text-lg bg-white text-rose-600"
            onClick={() => setShowYesScene(false)}
          >
            Tutup 💌
          </Button>
        </motion.div>
      )}

      {/* Main Card */}
      <motion.div
        initial={{ opacity: 0, scale: 0.8 }}
        animate={{ opacity: 1, scale: 1 }}
        transition={{ duration: 1 }}
        className="w-full max-w-xl relative z-10"
      >
        <Card className="rounded-3xl shadow-2xl bg-white/85 backdrop-blur-md">
          <CardContent className="p-6 md:p-8 space-y-6">
            <h1 className="text-2xl md:text-5xl font-bold text-rose-600">
              Misi Rahasia Untuk Mawar Sayang 💌
            </h1>

            <p className="text-base md:text-lg text-gray-700 min-h-[60px]">
              {messages[step]}
            </p>

            {step < messages.length - 1 && (
              <Button
                className="rounded-2xl px-6 py-4 text-base md:text-lg w-full"
                onClick={() => setStep(step + 1)}
              >
                Lanjut 👉
              </Button>
            )}

            {step === messages.length - 1 && (
              <div className="space-y-4">
                <p className="text-base md:text-lg font-semibold text-rose-700">
                  Sekarang tekan tombol ini pelan‑pelan ya...
                </p>
                <Button
                  className="rounded-2xl px-6 py-4 text-base md:text-lg shadow-lg w-full"
                  onClick={() =>
                    setLoveLevel((prev) => (prev < 100 ? prev + 20 : 100))
                  }
                >
                  Tambah Cinta <Heart className="ml-2" />
                </Button>

                <div className="w-full bg-gray-200 rounded-full h-4 overflow-hidden">
                  <motion.div
                    className="bg-rose-500 h-4"
                    animate={{ width: `${loveLevel}%` }}
                  />
                </div>

                {loveLevel >= 100 && (
                  <motion.div
                    initial={{ opacity: 0 }}
                    animate={{ opacity: 1 }}
                    className="space-y-4"
                  >
                    <p className="text-lg md:text-xl font-bold text-rose-600">
                      Boom 💥 Cintanya Full!
                    </p>
                    <Button
                      className="rounded-2xl px-6 py-4 text-base md:text-lg w-full"
                      onClick={() => setShowSecret(true)}
                    >
                      Buka Pesan Rahasia ✨
                    </Button>
                  </motion.div>
                )}

                {showSecret && (
                  <motion.div
                    initial={{ scale: 0.8, opacity: 0 }}
                    animate={{ scale: 1, opacity: 1 }}
                    className="p-6 bg-rose-100 rounded-2xl shadow-inner space-y-4"
                  >
                    <p className="text-base md:text-lg text-rose-800">
                      Sebenarnya website ini cuma alasan...
                      <br />
                      Alasanku cuma satu:
                    </p>
                    <p className="text-xl md:text-2xl font-bold text-rose-600">
                      Aku sayang banget sama kamu, Mawar ❤️
                    </p>

                    <Button
                      className="rounded-2xl px-6 py-4 text-base md:text-lg w-full"
                      onClick={() => setShowForeverPopup(true)}
                    >
                      Lanjut ke Pertanyaan Terakhir 😳
                    </Button>
                  </motion.div>
                )}
              </div>
            )}
          </CardContent>
        </Card>
      </motion.div>

      {/* Forever Popup */}
      {showForeverPopup && (
        <div className="fixed inset-0 bg-black/40 flex items-center justify-center z-50 p-4">
          <motion.div
            initial={{ scale: 0.7, opacity: 0 }}
            animate={{ scale: 1, opacity: 1 }}
            className="bg-white w-full max-w-md p-6 md:p-10 rounded-3xl shadow-2xl text-center space-y-6 relative"
          >
            <h2 className="text-xl md:text-3xl font-bold text-rose-600">
              Mawar Sayang 🌹
            </h2>
            <p className="text-base md:text-lg">
              Will you stay with me forever? 💍
            </p>

            <div className="relative flex items-center justify-center gap-4 md:gap-6 mt-6">
              <Button
                className="rounded-2xl px-6 py-4 text-base md:text-lg"
                onClick={() => {
                  setShowForeverPopup(false);
                  setShowYesScene(true);
                }}
              >
                Yes 💖
              </Button>

              <motion.div
                animate={{ x: noPosition.x, y: noPosition.y }}
                transition={{ type: "spring", stiffness: 300 }}
              >
                <Button
                  variant="outline"
                  onMouseEnter={moveNoButton}
                  onTouchStart={moveNoButton}
                  onClick={moveNoButton}
                  className="rounded-2xl px-6 py-4 text-base md:text-lg"
                >
                  No 🙈
                </Button>
              </motion.div>
            </div>
          </motion.div>
        </div>
      )}

      <motion.div
        initial={{ opacity: 0 }}
        animate={{ opacity: 1 }}
        transition={{ delay: 2 }}
        className="mt-8 text-xs md:text-sm text-rose-900 flex items-center gap-2 relative z-10"
      >
        Dibuat khusus untuk Mawar Sayang 🌹 <Sparkles size={16} />
      </motion.div>
    </div>
  );
}
