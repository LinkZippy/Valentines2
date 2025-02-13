
import { useState } from "react";
import { motion } from "framer-motion";
import { Button } from "@/components/ui/button";
import { Card } from "@/components/ui/card";
import FloatingHearts from "@/components/FloatingHearts";
import EvasiveButton from "@/components/EvasiveButton";
import confetti from 'canvas-confetti';

export default function Valentine() {
  const [showConfetti, setShowConfetti] = useState(false);

  const handleYesClick = () => {
    setShowConfetti(true);
    confetti({
      particleCount: 100,
      spread: 70,
      origin: { y: 0.6 },
      colors: ['#ff69b4', '#ff1493', '#ff0000']
    });
  };

  return (
    <div className="min-h-screen bg-pink-50 flex items-center justify-center relative overflow-hidden">
      <FloatingHearts />
      
      <Card className="w-full max-w-lg mx-4 p-8 bg-white/80 backdrop-blur-sm shadow-xl">
        <motion.div
          initial={{ scale: 0.5, opacity: 0 }}
          animate={{ scale: 1, opacity: 1 }}
          transition={{ duration: 0.5 }}
          className="text-center"
        >
          <h1 className="text-4xl md:text-5xl font-bold text-pink-600 mb-8">
            Will You Be My Valentine?
          </h1>

          <div className="flex flex-col md:flex-row gap-4 justify-center items-center mt-8">
            <Button
              onClick={handleYesClick}
              className="bg-pink-500 hover:bg-pink-600 text-white px-8 py-4 text-xl"
            >
              Yes
            </Button>

            <EvasiveButton />
          </div>

          {showConfetti && (
            <motion.p
              initial={{ opacity: 0, y: 20 }}
              animate={{ opacity: 1, y: 0 }}
              className="mt-8 text-2xl text-pink-600 font-semibold"
            >
              Yay! Happy Valentine's Day! ❤️
            </motion.p>
          )}
        </motion.div>
      </Card>
    </div>
  );
}
